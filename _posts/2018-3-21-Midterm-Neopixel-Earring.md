---
layout: post
title: "Midterm: Neopixel Earring"
categories: hardware
---
image

#### Schematic and Board Design ####

#### Parts List ####

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

#### Video Documentation of Interaction####
<iframe width="560" height="315" src="https://www.youtube.com/embed/rnmWxoutTYg" frameborder="0"allowfullscreen></iframe>
It works!!

#### Process and Mistakes ####

