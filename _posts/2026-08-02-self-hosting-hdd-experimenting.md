---
layout: post
title:  "Noisy self-hosting troubles"
date:   2026-08-01 10:00:00 +0200
categories: post
cover: /images/selfhosting-hdd-experiments/cover-title.webp
tags: ["Self-hosting", "3Dprint", "HDD", "Fun"]
introduction: 'Self-hosting is fun, but it takes a lot of work and time. It can be quite fun, until it is too much and you start feeling mad. Whether this sounds familiar to you or not, take a short read.'
featured: False
---

## How did it all start?

When you self-host you might want to host all kinds of services and some of them take a lot of disk space. On one of my servers the 256 GB NVMe started to feel quite tight. Funny/sad thing is that the server has the largest disk of all of my serverss.

I had two 3.5" internal 1 TB WD Gold that were slying around and one 3.5" 2 TB Seagate Barracuda. I briefly tested all of them and found out the WD Gold wass much quieter. That is very important to me as all my current viable server locations are in living spaces and the whole story revolves around keeping it quiet.

## Which drive should I use?

I had a dilemma. I could use the noisier desktop-grade Barracuda or smaller server-grade Gold. I decided to go for a third option, using an external dual bay. The disadvantage of the bay is that it is completely enclosed, so I took my time. I designed and 3D printed an open cover to let the heat escape better. [**I uploaded the model to printables!**](https://www.printables.com/model/1797295)

<center>
<img src="/images/selfhosting-hdd-experiments/orico-case3259u3-case.webp"  width="39%"/>
</center>

To my horror, I found that, no matter if used with open or closed cover, the drives became much louder when installed in the case. I still didn't give up and I tried the Barracuda drive in a different case and it was actually quieter. So it was not only the noise from the drive, but also vibration and other factors were involved. 

## HDD mounts

I modeled and printed mounts specifically for a hard-drive mounting system. The mounts I found online didn't match my screws. I mounted the drive and voila! Everything fit and worked fine, but it was still noisy 😫 I have noticed that the original HP mounts do have rubber isolators incorporated to minimise the vibration transferred from the drive to the rest of the PC. 

<center>
<img src="/images/selfhosting-hdd-experiments/all-hdd-mounts-crop.webp"  width="29%"/>
<img src="/images/selfhosting-hdd-experiments/rubber-mount-prepared.webp"  width="29%"/>
<img src="/images/selfhosting-hdd-experiments/rubber-mount-screwed.webp"  width="29%"/>
</center>

As illustrated in the pictures, the trick is to not use the rubber isolation in one point but in two. One inside and one outside as the vibrations travel not only through the drive side contact but also through the screw, thus it is necessary to isolate all contacts! I have used regular rubber band (yellow) that you use in the kitchen to close plastic bags. [**I uploaded the models to printables!**](https://www.printables.com/model/1797231)

I have designed the vibration damping mounts and the situation improved considerably! Success 🥳 ... no not so much.

<center>
<img src="/images/selfhosting-hdd-experiments/server-hdd-view.webp"  width="39%"/>
</center>

## Change of plans

The rubber mounts really improved the situation, but it is still a spinning chunk of metal and it still makes noise no matter what. Sad and frustrated, I castrated my "retro" project PC and removed a 500 GB SATA SSD from it and put it in the server. I haven't even had the energy to print a proper adapter and I fixed it with zip ties 🙃😃 It is ugly, but it does not matter because it stays quiet 💤

<center>
<img src="/images/selfhosting-hdd-experiments/server-sdd-view.webp"  width="39%"/>
</center>