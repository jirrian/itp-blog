---
layout: post
title: "A New Sense: Do I Need My Umbrella Today?"
categories: wearables
---

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light.jpg)
Every morning, I ask my boyfriend outloud, "What is the weather today?". And then I have to check by opening my phone which can sometimes be tedious when I'm in a rush. Most of the time, I don't check at all and don't bring an umbrella when I need to. Typically, I get caught in the rain and have to call an overpriced Uber.

For this project, I tried to make an attachment for my umbrella that simply notifies me if I need to use it today. This attachment gives a simple yes or no answer to the question "Do I need to take my umbrella with me today?". It connects to WiFi, gets the daily forcast, and if it is going to rain or snow, lights up the LED, catching my eye while I'm heading out the door. If there is no predicted rain or snow, the LED doesn't light up.
This project is kind of inbetween a wearable and IoT. My design is to make the board attachable to any umbrella you choose rather that to integrate it into the umbrella itself.

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light2.jpg)

#### PCB Design ####
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_sch.png)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_board.png)

#### Fabrication Process ####
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_milling.jpg)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_pcb.jpg)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_soldering.jpg)

#### Programming ####
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_feather.jpg)

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_prog.jpg)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/arduinoide.png)
[previous project](http://blog.jzhong.today/electronicrituals/Digital-Amulet-Programming/)

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/serial.png)

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_board.jpg)

[weather api](https://www.weatherbit.io/api/weather-forecast-16-day)
[code](https://github.com/jirrian/umbrella_light/blob/master/umbrella_light_prototype.ino)

#### Prototype Enclosure ####
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_enclosure_proto1.jpg)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_enclosure_proto2.jpg)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/enclosure_example.jpg)


