---
layout: post
title:  "Phone localization using computer vision for Dowry Towns of Bohemian Queens "
date:   2021-05-15 08:37:34 +0100
categories: jekyll update
cover: /images/phone-localization/phone-localization-cover.png
---

**The work was a bachelor thesis created as a part of the Dowry Cities of Czech Queens project, which aims to bring history closer to the general public using modern technologies such as augmented reality. This is done using an application for Android mobile devices, which displays historical elements in the camera scene at runtime. This work contributes to its development by proposing a localization solution for the application using image and geolocation data.**

**[The github repository](https://github.com/PavelKriz/phone-localization) of the solution.**

- **Application goal:** visualize historical look of already changed buildings (and other projects)
- **Implemented part:** accurate localization solution
- **Solved problem:** insufficient accuracy of phones GPS, compass and gyroscope sensors  
- **Used technologies:** `C`, `C++`, `OpenCV`, `Boost`

## Results

The resulting localization accuracy is higher by using this solution than by using GPS and other mobile sensors. The accuracy was tested on multiple tests and the accuracy gain by using the **implemented solution was on average 11.94 meters more accurate than GPS** It can be visualized by following example. 

<div style="text-align:center">
<p float="left" >
<img src="/images/phone-localization/Vrsovice2_loc.jpg"  width="39%"/>
<img src="/images/phone-localization/Vrsovice2_vol.jpg"  width="39%"/>  
</p>
</div>

On the left is aerial map and on the right is the detected location of localized house.
- **yellow line**: house facade
- **green pin**: calculated location
- **cyan pin**: GPS sensor location


