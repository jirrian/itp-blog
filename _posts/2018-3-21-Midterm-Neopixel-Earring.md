---
layout: post
title: "Midterm: Neopixel Earring"
categories: hardware
---

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/homemadehardware/midterm/earring_final.jpg)
I made a battery powered earing with neopixels. My goal for this assignment was to learn how to use surface mount components so I kept the design and functionality simple.

#### Schematic and Board Design ####
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/homemadehardware/midterm/neopixel_earring_sch.png)
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/homemadehardware/midterm/neopixel_earring_brd.png)

#### Parts List ####
* WS2812B neopixel (7)
* 0.1μF capacitor (7)
* ATTiny85
* [coin cell battery holder](https://www.amazon.com/gp/product/B01J5FY2GI/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1)
* 3V coin cell battery

#### Code ####
I used Adafruit's example code for neopixels and adapted it for my needs. I turned the brightness down since I'm only powering it with a 3V coin cell battery.

```c++
#include <Adafruit_NeoPixel.h>

int pin = 3;
int len = 7;

Adafruit_NeoPixel strip = Adafruit_NeoPixel(len, pin, NEO_GRB+ NEO_KHZ800);

void setup() {
  strip.begin();
  strip.show();
  strip.setBrightness(20);
}

void loop() {
  rainbowCycle(20);
}

/*
  from adafruit's strandtest example
*/

// Slightly different, this makes the rainbow equally distributed throughout
void rainbowCycle(uint8_t wait) {
  uint16_t i, j;

  for(j=0; j<256*5; j++) { // 5 cycles of all colors on wheel
    for(i=0; i< strip.numPixels(); i++) {
      strip.setPixelColor(i, Wheel(((i * 256 / strip.numPixels()) + j) & 255));
    }
    strip.show();
    delay(wait);
  }
}


// Input a value 0 to 255 to get a color value.
// The colours are a transition r - g - b - back to r.
uint32_t Wheel(byte WheelPos) {
  WheelPos = 255 - WheelPos;
  if(WheelPos < 85) {
    return strip.Color(255 - WheelPos * 3, 0, WheelPos * 3);
  }
  if(WheelPos < 170) {
    WheelPos -= 85;
    return strip.Color(0, WheelPos * 3, 255 - WheelPos * 3);
  }
  WheelPos -= 170;
  return strip.Color(WheelPos * 3, 255 - WheelPos * 3, 0);
}
```

#### Process ####
I had to remill the board several times while making the dimensions larger so that the ground plane would not get disconnected.
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/homemadehardware/midterm/millprocess.jpg)

After placing surface mount components and reflow:
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/homemadehardware/midterm/smc.jpg)

I left pads to solder wires to that connect to my Arduino Uno to program the ATTiny85. While programming, something went wrong and I could no longer get a device signature from my ATtiny85. I ended up replacing it with another one which worked.
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/homemadehardware/midterm/programming.jpg)

#### Mistakes in Board Design ####
After receiving the battery holders, I found out that they are different from the part I used in the board design. The ground pin is on the side and not in the center (as it is in the board design file). I soldered a wire to connect the ground plane in the center to the side plane which was not connected to anything. I then soldered the battery holder on top of that.
While programming, I realized I also made a mistake in the board design and forgot to add an external pull-up resistor to VCC on the reset pin of the ATTiny85. I also did not add a resistor before my first neopixel which is recommended by Adafruit.

#### Documentation Images ####
<iframe width="560" height="315" src="https://www.youtube.com/embed/rnmWxoutTYg" frameborder="0" allowfullscreen></iframe>
