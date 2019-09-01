---
layout: post
title: "A New Sense: Do I Need My Umbrella Today?"
categories: wearables
---

![alt text](/images/wearables/umbrella_light/umbrella_light.jpg)
Every morning, I ask my boyfriend outloud, "What is the weather today?". And then I have to check by opening my phone which can sometimes be tedious when I'm in a rush. Most of the time, I don't check at all and don't bring an umbrella when I need to. Typically, I get caught in the rain and have to call an overpriced Uber.

For this project, I tried to make an attachment for my umbrella that simply notifies me if I need to use it today. This attachment gives a simple yes or no answer to the question "Do I need to take my umbrella with me today?". It connects to WiFi, gets the daily forcast, and if it is going to rain or snow, lights up the LED, catching my eye while I'm heading out the door. If there is no predicted rain or snow, the LED doesn't light up.
This project is kind of inbetween a wearable and IoT. My design is to make the board attachable to any umbrella you choose rather that to integrate it into the umbrella itself.

![alt text](/images/wearables/umbrella_light/umbrella_light2.jpg)

#### PCB Design ####
A created a simple schematic with a ESP8266 module, APA102 LED, and a 3V battery.
![alt text](/images/wearables/umbrella_light/umbrella_light_sch.png)
![alt text](/images/wearables/umbrella_light/umbrella_light_board.png)

#### Fabrication Process ####
I fabricated the board on the Othermill. I had to hand solder the components on the board because I couldn't find solder paste. That's why the board came out so messy.
![alt text](/images/wearables/umbrella_light/umbrella_light_milling.jpg)
![alt text](/images/wearables/umbrella_light/umbrella_light_pcb.jpg)
![alt text](/images/wearables/umbrella_light/umbrella_light_soldering.jpg)

The trace connecting one of the ATTiny85 pins to the APA102 LED peeled off. I then decided to switch to a regular blue LED because one pin and ground could still be connected. This makes the design back to a binary yes or no answer, which is okay. If I were to expand the design further with the APA102, I could use different colors to signify rain or snow for example.

#### Programming ####
I prototyped the programming with a Adafruit Feather HUZZAH which has the same wifi module that I'm using on my custom board.
![alt text](/images/wearables/umbrella_light/umbrella_light_feather.jpg)

I based the code off of the [HTTPSRequest example](https://github.com/esp8266/Arduino/blob/master/libraries/ESP8266WiFi/examples/HTTPSRequest/HTTPSRequest.ino). The program simply grabs data from a [weather api](https://www.weatherbit.io/api/weather-forecast-16-day) for the weather in New York today. It checks the [weather codes](https://www.weatherbit.io/api/codes) returned to see if it's raining or snowing. If the code is less than 700, then it's raining or snowing.

[see the code here](https://github.com/jirrian/umbrella_light/blob/master/umbrella_light_prototype.ino)

I soldered wires onto pads connected to the pins on the ESP8266 so that the module could be programmed. See [this post](http://blog.jzhong.today/electronicrituals/Digital-Amulet-Programming/) for more detailed instructions on how to program this module.
![alt text](/images/wearables/umbrella_light/umbrella_light_prog.jpg)

I used these settings in the Arduino IDE:
![alt text](/images/wearables/umbrella_light/arduinoide.png)

Example of serial output from code:
![alt text](/images/wearables/umbrella_light/serial.png)

The LED lights up if the data from the api says it's raining or snowing.
![alt text](/images/wearables/umbrella_light/umbrella_light_board.jpg)

#### Prototype Enclosure ####
I glued these plastic strings to the back so the board could be tied to any umbrella handle. I did this so that the board could be attached different umbrellas.
![alt text](/images/wearables/umbrella_light/umbrella_light_enclosure_proto1.jpg)
![alt text](/images/wearables/umbrella_light/umbrella_light_enclosure_proto2.jpg)

I imagine the final enclosure to be some kind of waterproof silicone sleeve, similar to these hand sanitizer holders:
![alt text](/images/wearables/umbrella_light/enclosure_example.jpg)

