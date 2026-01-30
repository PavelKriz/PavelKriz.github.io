---
layout: post
title:  "Kubernetes Runner"
date:   2026-01-29 15:03:00 +0100
categories: jekyll update
cover: /images/simple_kubernetes_GitLab-runner/cover.jpg
tags: ["Kubernetes", "DevOps", "GitLab", "GitLab Runner", "MicroK8s", "CI/CD"]
introduction: 'With the deprecation of GitLab Docker runner, the simple runner solution for small teams or standalone developers is no longer the way. The Kubernetes runner is the other containerized option which might seem complicated at first but actually it is not.'
---

[As GitLab deprecated the docker executor](https://docs.gitlab.com/runner/executors/docker_machine/):

> The Docker Machine executor was deprecated in GitLab 17.5 and is scheduled for removal in GitLab 20.0 (May 2027). 

one of the two simple options for runner are now gone, one of which is docker runner and the other shell runner. But as shell runner runs into problem even when using only by one developer. Talking about security not being concern in one manned team but the environment is then kept the same for all jobs. 

**Fortunately there is a Kubernetes executor runner**. This might seem complicated at first, but it is not if we choose the right Kubernetes implementation. Well installing regular Kubernetes will be big overkill for small or one manned team, but there are also smaller installs of it like minikube. However minikube is not meant to be production ready, thus stuff like K3s or microK8s come into play. They can to be installed into both one node mode or multi-node mode. As K3s is quite powerful and easy to install it is not as straightforward as microK8s. **With microK8s you just install with snap and we have set up Kubernetes**.

Well if we have snap availible just running is enough:

```bash
snap install microk8s --classic
```

Now we have very easy live, we have all setup up and working. Kubectl and Helm are just availible like so:

```bash
microk8s kubectl get pod --all-namespaces
microk8s helm list --all-namespaces
```

and if we even need we are not stopped if we need to automate it as we can access the same directly with binaries. 

As a last step we just install the runner with a helm chart as it come prebundled already!

## Is it all really that great?

Yes and not, it all depends on the needs. One big downside is the fact that it is more a plug and play installation very suitable for experiments and such stuff as updates might be cumbersome. However we do have very good experience with it even in extensively used environments and as it cannot be updated as easily is not as a big of downside in case of runners as they do not keep any persistent settings other then these stored in manifests (our `.yaml`configs).