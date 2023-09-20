---
layout: post
title:  "PACMAN - a game that runs even on 3 FPS"
date:   2020-06-17 17:37:34 +0100
categories: jekyll update
cover: /images/Configurable_pacman/cover.png
---

**Introducing "PACMAN" – a game that defies expectations by running smoothly even at a mere 3 FPS! Its coded to be playable and reliable under such condition. This classic arcade game has been given a modern twist, featuring customizable maps, various game modes, and a unique challenge involving the pursuit of "covid".**

**[The github repository](https://github.com/PavelKriz/LBP_GIMP_plugin) of the game contains more information and the game itself.**

<style>

.container{
      position: relative;
      width: 50%;
}

.image {
  display: block;
  width: 100%;
  height: auto;
}

.overlay {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100%;
  width: 100%;
  opacity: 0;
  transition: .5s ease;
  background-color: #000000;
}

.upper_overlay {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  height: 20%;
  width: 100%;
  opacity: 0;
  transition: .5s ease;
  background-color: #000000;
}


.container:hover .overlay {
  opacity: 0.7;
}

.container:not(:hover) .overlay{
  height: 10%;
  opacity: 0.5;
}


@media only screen and (max-width: 1000px) {
  .text {
  color: white;
  font-size: 3vw;
  position: absolute;
  top: 3%;
  left: 3%;
}
}

@media only screen and (min-width:1001px) { 
.text {
  color: white;
  font-size: 1vw;
  position: absolute;
  top: 3%;
  left: 3%;
}
}
</style>


<div class="container" style="float: left">
  <img src="/images/Configurable_pacman/pacman.png"  class="image">

  <div class="overlay">
    <div class="text">Graphics <br> the game uses the sdl2 library for c++ in 2D mode </div>
  </div>
</div>

<div class="container" style="float: right">
  <img src="/images/Configurable_pacman/pacman_live_lost.png"  class="image">
  <div class="overlay">
    <div class="text">On a hunt <br> Eat all the points on the map while being hunted by the ghosts. Try to eat the big points and eat them down as well</div>
  </div>
</div>


<div class="container" style="float: left">
  <img src="/images/Configurable_pacman/map.png"  class="image">
  <div class="overlay">
    <div class="text">Create your map <br> Using the map config file you can create the levels yourself as you wish</div>
  </div>
</div>


<div class="container" style="float: right">
  <img src="/images/Configurable_pacman/pacman_covid.png"  class="image">
  <div class="overlay">
    <div class="text">Hard mode <br> The covid hunts you in the hardest mode of the game. </div>
  </div>
</div>

<div class="container" style="float: right">
  <img src="/images/Configurable_pacman/config.png"  class="image">
  <div class="overlay">
    <div class="text">Configurable game <br> You can configure multiple parameters that determines the hardness of the game or the mode of the game</div>
  </div>
</div>

<div class="container" style="float: left">
  <img src="/images/Configurable_pacman/pacman_level_done.png"  class="image">
  <div class="overlay">
    <div class="text">Next level <br> You go to next level when you collect all the points on the map. The next level is harder accordingly</div>
  </div>
</div>


<div style="clear: both;"></div> 

<div style="margin-bottom: 2cm;">
</div>



<br>
