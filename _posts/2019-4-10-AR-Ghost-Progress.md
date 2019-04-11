---
layout: post
title: "AR Ghost Sculpture Progress"
categories: videosculpture
---

I'm working on this piece as part of my thesis. The concept is to create a ghostly figure that has presence in the room through AR. I want to see if I can use synthetic and artifical objects (3D models of cartoonish robots and anime girls found online) and give the perception of life and personhood. The 'ghost' is supposed to be human scale and stand idly in the space. When you walk close enough to it, it should turn to face you.

Much of my time so far was spent learning how to use Blender. I originally wanted to create some sort of Frankenstein looking humanoid using multiple models of anime style models but my 3D modeling skills were not experienced enough. I created a hybrid between a human and a robot. It was always intented to not have a face. It currently does not have any materials on it but I do like the transparent, ghostly look.

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/videosculpture/ghost/blender.png)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/videosculpture/ghost/blender_tpose.png)

Rigging and animations were done in Mixamo:
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/videosculpture/ghost/mixamo.png)

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/videosculpture/ghost/unity.png)

This is still a work in progress. I need to add the user interaction as well as find a better workflow for developing the rest of this project. Vuforia ground plane detection is not available for my phone: OnePlus 6, making it really hard for me to test this. I ended up using my old phone, a Nexus 6P to upload the build to. This phone is super laggy and detected the ground plane really slowly. Not to mention it was really hard for me to even take a screenshot for documentation. The battery also kept running out as it's probably at the end of it's lifespan; I kept having to switch between charging the phone with a wall charger and moving it to the cord attached to the computer to install the build. I need to find another device I can test on and take screen recording documentation on. In the meantime, I will print out the Vuforia ground plane tracker and use it with the webcam.

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/videosculpture/ghost/vuforia_test.png)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/videosculpture/ghost/vuforia_test2.png)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/videosculpture/ghost/vuforia_test3.png)

Because of the unconvience of testing on the old Nexus 6P, the current model scale is way too large and needs to be tweeked.
