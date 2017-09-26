---
layout: post
title: Digital Input and Output
categories: pcomp
---

I began by completing the [digital input and output lab](https://itp.nyu.edu/physcomp/labs/labs-arduino-digital-and-analog/digital-input-and-output-with-an-arduino/){target="_blank"} on the ITP PComp syllabus.
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/IMG_20170926_005934.jpg)

This circuit changes which LED lights up based on whether the switch is pushed down or not. I combined this idea with the [Arduino tutorial 'fade' example](https://www.arduino.cc/en/Tutorial/Fade){target="_blank"}. In this example, an increasing and decreasing brightness value is passed to an LED, fading it brighter and then dimmer.

My application has 2 switches and 1 LED. When one switch is pressed, the LED gets brighter (max at max brightness value 255). When the other switch is pressed, the LED gets dimmer (min at minimum brightness value 0).

Circuit and connections with LED shown at max brightness:
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/IMG_20170926_014702.jpg)
The LED is connected at pin 9.
Switch 1 (brightens) is connected at pin 4.
Switch 2 (dims) is connected at pin 2.


