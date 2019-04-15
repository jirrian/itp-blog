---
layout: post
title: "Umbrella Notification Light Update"
categories: wearables
---

I've added some improvements to the code that make this board actually usable for it's design. The main one is that I now put the board to sleep after making the https request. This is to improve the battery life of the coin cell.

Before, the code connected to wifi, made an https request, parsed the json feedback, and turned on the LED accordingly. It only did this once. Now, it should update based on the weather api every 12 hours.

![alt text](https://cloud.githubusercontent.com/assets/2480569/8272121/91084536-1837-11e5-9a53-52ff89969f7c.png)
[photo from here](https://github.com/esp8266/Arduino/issues/460)

At first, I tried putting the board into deep sleep. This turns off all of the ESP8266 except for the RTC circuit (real time clock) so that it can wake itself up. I followed [this tutorial](https://randomnerdtutorials.com/esp8266-deep-sleep-with-arduino-ide/) and connected the GPIO16 pin to the Reset pin.
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_gpio16_to_reset.jpg)

I then added this line to the end of my existing code `ESP.deepSleep(43200000);` so that the chip would go to sleep for 12 hours.
I tested this with 30 seconds at first and it worked! The board will connect to wifi, make the https request, and turn on the LED. Then, it sleeps for 30 seconds before restarting and running the code again. The only problem is that the LED also turns off during deep sleep.

So, I decided to try modem sleep mode. This just turns off the wifi functionalities of the chip.
I put the code into a loop and added this at the end inside the loop:

```c++
  WiFi.disconnect();
  WiFi.forceSleepBegin();
  delay(43200000);
  
  WiFi.forceSleepWake();
 ```
I found this information in [this github thread](https://github.com/esp8266/Arduino/issues/460#issuecomment-168775857). Now, the wifi is supposed to turn off for 12 hours and wake up again afterwards. I tested it with 30 seconds and it worked. The LED stays on during modem sleep because only the wifi is being turned off.

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_ledon.jpg)

[github link to code](https://github.com/jirrian/umbrella_light)

I'm not sure how much battery this saves compared to deep sleep. I still need to test the battery life of this board by just leaving it connected and running.

I also worked on a possible enclosure design for this project:
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/wearables/umbrella_light/umbrella_light_enclosure_sketch.jpg)

