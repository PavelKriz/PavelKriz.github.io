---
layout: post
title:  "Automated GitLab deployment in Cloud"
date:   2025-03-23 18:25:45 +0100
categories: jekyll update
cover: /images/AutomatedGitLabDeployment/cover.png
tags: ["DevOps", "GitLab", "GitLab Omnibus", "Teraform", "HAProxy", "Docker", "Automated certificates"]
introduction: 'A concept demonstration of unusual tech-stack fto deploy GitLab or any similar service.'
---

Why a interesting stack? Normally we would not use terraform (or OpenTofu) for such stuff, but rather use Docker Compose or Dockerfile. But maybe that is not what is the used stack, so for a demonstration we can use Terraform as well and a `kreuzwerker/docker` provider for infrastructure. This way we can manage containers locally instead of VMs. Another challange of this tech concept is not to use something more automated like `Traefik` as a proxy but rather manually set up our routing with `HAProxy` and automate the certificate ourselves with `Certbot`.

This short article will go over the terraform file which will show most of the connections and principles. The rest of the implementation is omitted for simplicity.

## 1. HAProxy

First get all stuff like provider and images then start with HAProxy itself. Lets start with it as other container depends on it:

```tf
resource "docker_container" "external_load_balancer" {
  image = docker_image.haproxy.image_id
  name  = "external_load_balancer"
  restart = "always"
  ports {
    internal = 80
    external = 80
  }
  ports {
    internal = 443
    external = 443
  }
  ports {
  	internal = 22
  	external = 22
  }
  networks_advanced {
  	name = docker_network.gitlab_network.name
  }
  mounts {
  	source = "/MY_PROJECT_PATH/gld/data/certs/deploy-certs/"
  	target = "/deploy-certs/"
  	type = "bind"
    read_only = true
  }
  mounts {
    source = "/MY_PROJECT_PATH/gld/haproxy.cfg"
    target = "/usr/local/etc/haproxy/haproxy.cfg"
    type = "bind"
    read_only = true
  }
}
```

The ports noted are all the ports needed for GitLab, however Certbot is needing 80 port as well. This can be solved by HAProxy rule in its config to route requests on `/.well-known/acme-challenge/` subpath to Certbot. We cannot forgot about mounting the certificates so we can use them in HAProxy as well as the config. 


## 2. GitLab 

GitLab itself is not hard to deploy on docker. Lets take a look on the deployment:

```tf
resource "docker_container" "gitlab" {
  image = docker_image.gitlab.image_id
  name  = "gitlab"
  restart = "always"
  depends_on = [
  	docker_container.external_load_balancer
  ]
  networks_advanced {
  	name = docker_network.gitlab_network.name
  }
  mounts {
  	source = "/MY_PROJECT_PATH/gld/data/gitlab/config"
  	target = "/etc/gitlab"
  	type = "bind"
  }
  mounts {
    source = "/MY_PROJECT_PATH/gld/data/gitlab/logs"
    target = "/var/log/gitlab"
    type = "bind"
  }
  mounts {
    source = "/MY_PROJECT_PATH/gld/data/gitlab/data"
    target = "/var/opt/gitlab"
    type = "bind"
  }
}
```

Note that gitlab depends on external load balancer and we have to bind all the three directories.


## Busybox server

Before the last step we have to install the simplest webserver possible, `bussybox httpd`. That is because we are going to use the http challange of the acme protocol. This will be great because of **zero downtime** for the certificate renewal.

```tf
resource "docker_container" "busybox_httpd" {
  image = docker_image.busybox.image_id
  name  = "busybox_httpd"
  restart = "always"
  networks_advanced {
  	name = docker_network.gitlab_network.name
  }
  mounts {
    source = "/MY_PROJECT_PATH/gld/data/certs/www"
    target = "/var/www"
    type = "bind"
    read_only = true
  }
  command = [
  	"httpd", "-f", "-v", "-p", "80", "-h", "/var/www"
  ]
}
```

Note that we have to mount the webpages folder shared with Certbot. 


## Certbot

As the last step we are going to spin up the Certbot container that will move the files to the served folder and will take care of the certificate request and renewal.


```tf
resource "docker_container" "certbot"  {
  image = docker_image.certbot.image_id
  name = "certbot"
  restart = "always"
  depends_on = [
  	docker_container.external_load_balancer
  ]
  networks_advanced {
  	name = docker_network.gitlab_network.name
  }
  mounts {
    source = "/MY_PROJECT_PATH/gld/data/certs/www"
    target = "/var/www/"
    type = "bind"
  }
  mounts {
    source = "/MY_PROJECT_PATH/gld/data/certs/letsencrypt"
  	target = "/etc/letsencrypt/"
  	type = "bind"
  }
  mounts {
    source = "/MY_PROJECT_PATH/gld/data/certs/deploy-certs"
  	target = "/deploy-certs"
  	type = "bind"
  }
  mounts {
  	source = "/MY_PROJECT_PATH/gld/cert-deploy-script.sh"
  	target = "/etc/letsencrypt/renewal-hooks/deploy/cert-deploy-script.sh"
  	type = "bind"
    read_only = true
  }
  command = [
    "certonly", "--webroot", "--webroot-path", "/var/www", 
    "--non-interactive", "--agree-tos", "-m", "gitlab-team@example.com", 
    "-d", "my-gitlab.example.com",
  ]
}
```

Here we can see, that we don't only make the interconnection with HAProxy to pass it the certificates, but we have to use the webserver path to serve the files for the acme challenge to renew certificates.


## Why and why not

This is probably not the most common solution to do the same functionality. We can imagine tech-stack such as *Traefik*, *docker-compose* and *GitLab* all in docker to fill in the same functionality. However the stack might not be available, or this one might suit better the overall tech or skills. One big advantage is the ease of change to VMs, just one has to implement shared storage. Also proxy like *HAProxy* is more performant then *Traefik*.