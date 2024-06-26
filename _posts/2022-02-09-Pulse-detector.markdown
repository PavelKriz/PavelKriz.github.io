---
layout: post
title:  "Webcam pulse detector - live heart rate detection"
date:   2022-02-09 11:06:34 +0100
categories: jekyll update
cover: /images/Pulse_detector_images/cover.png
tags: ["Python", "OpenCV"]
introduction: "Are you curious about measuring your pulse using just a webcam? Dive into the world of pulse detection with PULSE DETECTOR, a Python application built on OpenCV. This project offers a glimpse into how your webcam can reveal your pulse frequency. Join us as we explore the application's features, accuracy, and installation instructions."
github: "https://github.com/PavelKriz/pulse_detector"
---


## Idea
Main idea is about creating application in Python, that would detect and display the pulse frequency. The output values are between 55 and 170 for one person.

## Descritption
The application looks like this:

<img src="/images/Pulse_detector_images/Pulse_detector.png"
            width="80%">
	
In the previous image can be seen the main part of the application, which is displayed in two windwos. The camera settings is easy and with the face locking mechanism is visible on the next images: 

<img src="/images/Pulse_detector_images/Pulse_detector_camera_setup.jpg"
             width="40%">
	    
<img src="/images/Pulse_detector_images/Pulse_detector_face_setup.jpg"
             width="40%">
            
It is good to note, that on first sight unpractical face locking, is actualy important for the accuracy of meassurements.

### Accuracy

  The accuracy was tested with the fitness armband Fitbit Charge 4, which meassures heartrate on the wrist (quite accurate armband at the time). It was shown that the accuracy of the meassurements is only approximate (same as in other seen and tested solutions) and mainly depends on the camera quality and video compression. It was tested on four cameras total on which three gave normal accuracy (among the set) and using one of them the application gave much more accurate results. 

There is one image frm testing which shows happy case, when the detections matches (the real one still might be bit different):

<img src="/images/Pulse_detector_images/happy.jpg"
             width="30%">
	
On this image the innacuracy is visible. The overall is wrong, but at the moment, the current pulse was meassured correctly (most dominant frequency):

<img src="/images/Pulse_detector_images/not_so_happy.jpg"
             width="30%">
	
## Installation and run
The `Python 3` is needed with the installed package `opencv-python` (tested with version 4). To run the program it is needed to type `python3 ./pulse_detector.py` in the correct folder in terminal.

## Other already created solutions at the time
There are already existing solutions for that, one of them is <a href="https://github.com/thearn/webcam-pulse-detector">webcam-pulse-detector</a>. That one is in Python, but there is also one in <a href="https://github.com/serghov/heartRate">Javascript</a>. Most detectors (our as well) uses forehead as detecting zone, but <a href="https://www.youtube.com/watch?v=IV51CYZsBOU">this one</a> uses cheeks. 
