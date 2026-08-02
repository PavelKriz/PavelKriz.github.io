---
layout: page
title: About
list_title: About
permalink: /about/
---

<img class="rounded-img" style="float: right;" width="20%" src="/images/Pavel_Kriz_web_full_small.jpg">

My name is Pavel Kříž, and at work I am a platform and software engineer with hands-on experience improving developer experience, running large-scale production-critical services, and developing software and tooling. My journey began at university, where I studied computer graphics, and evolved through pure software engineering before I found myself in platform engineering.

When I find some free time, I like to share some of my projects and experiences in these posts. However, I like to write them myself, without AI 😯, to keep the blog personal, so it takes quite some time. I began by posting about some interesting projects I took part in at university. Nowadays, I post about what I do and what I like to spend my free time on. From a technology perspective, that includes:
- developing fun projects
- self-hosting 
  - docker or kubernetes
- running services in cloud
- smart home
- 3D printing
- and others 

Apart from those, I also like to talk about my experiences and tech opinions.

<ul class="social-media-list">
  {%- if site.dribbble_username -%}<li><a href="https://dribbble.com/{{ site.dribbble_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#dribbble' | relative_url }}"></use></svg> <span class="username">{{ site.dribbble_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.facebook_username -%}<li><a href="https://www.facebook.com/{{ site.facebook_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#facebook' | relative_url }}"></use></svg> <span class="username">{{ site.facebook_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.flickr_username -%}<li><a href="https://www.flickr.com/photos/{{ site.flickr_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#flickr' | relative_url }}"></use></svg> <span class="username">{{ site.flickr_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.github_username -%}<li><a href="https://github.com/{{ site.github_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#github' | relative_url }}"></use></svg> <span class="username">My profile on GitHub</span></a></li>{%- endif -%}
  {%- if site.instagram_username -%}<li><a href="https://instagram.com/{{ site.instagram_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#instagram' | relative_url }}"></use></svg> <span class="username">{{ site.instagram_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.linkedin_username -%}<li><a href="https://www.linkedin.com/in/{{ site.linkedin_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#linkedin' | relative_url }}"></use></svg> <span class="username">My profile on LinkedIn</span></a></li>{%- endif -%}
  {%- if site.pinterest_username -%}<li><a href="https://www.pinterest.com/{{ site.pinterest_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#pinterest' | relative_url }}"></use></svg> <span class="username">{{ site.pinterest_username| escape }}</span></a></li>{%- endif -%}
  {%- for mst in site.mastodon -%}{%- if mst.username and mst.instance -%}<li><a href="https://{{ mst.instance| cgi_escape | escape}}/@{{mst.username}}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#mastodon' | relative_url }}"></use></svg> <span class="username">{{ mst.username|escape }}</span></a></li>{%- endif -%}{%- endfor -%}
  {%- if site.twitter_username -%}<li><a href="https://www.twitter.com/{{ site.twitter_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#twitter' | relative_url }}"></use></svg> <span class="username">{{ site.twitter_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.youtube_username -%}<li><a href="https://youtube.com/{{ site.youtube_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#youtube' | relative_url }}"></use></svg> <span class="username">{{ site.youtube_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.googleplus_username -%}<li><a href="https://plus.google.com/{{ site.googleplus_username| escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#googleplus' | relative_url }}"></use></svg> <span class="username">{{ site.googleplus_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.rss -%}<li><a href="{{ 'feed.xml' | relative_url }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#rss' | relative_url }}"></use></svg> <span>{{ site.rss | escape }}</span></a></li>{%- endif -%}
</ul>