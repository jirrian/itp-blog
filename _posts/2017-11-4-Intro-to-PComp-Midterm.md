---
layout: post
title: "Intro to PComp Midterm: Private Beach"
categories: pcomp
---
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/midterm/setup_prettyparts.jpg)

#### Concept ####
The concept was to hear sounds from a shell only when it's at your ear. A large projection of a visualization would appear when the shell is picked up but the accompanying sound can only be heard if you have the shell to your ear.

I wanted to explore private spaces vs. public spaces and private individual experiences within a collective experience.

The shell enclosure was integral to the concept from the beginning. I later developed ideas for the visualization and audio components.

#### Physical Interaction ####
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/midterm/sketch.jpg)

I originally planned to use the accelerometer built into the Arduino 101 to detect if the shell was faced down or being held up. This is what I used to build the prototype. I used [example code from Arduino](https://www.arduino.cc/en/Tutorial/Genuino101CurieIMUAccelerometerOrientation){:target="_blank"} to output the orientation of the board as integers. I then played a note using the Tone library if the orientation was not 0 (board is flat faced up).

I ran into problems when trying to incorporate audio. I was originally thinking I could play .wav files using a SD card breakout board but the [TMRpcm library](https://github.com/TMRh20/TMRpcm){:target="_blank"} is not compatible with the Arduino 101. I then purchased the [Adafruit VS1053 MP3/AAC/Ogg/MIDI/WAV Codec Breakout Board](https://learn.adafruit.com/adafruit-vs1053-mp3-aac-ogg-midi-wav-play-and-record-codec-tutorial/overview){:target="_blank"}, but again the VS1053 library is not currently updated to work with the 101.

Instead of figuring out how to adapt the library (something I know nothing about), I decided to just switch to the Arduino Uno and redo the accelerometer code. I used a separate 3-axis accelerometer, the [Adafruit ADXL335](https://learn.adafruit.com/adafruit-analog-accelerometer-breakouts){:target="_blank"}. I used a [custom ADXL335 library](https://github.com/codedecaybr/ADXL335){:target="_blank"} to make it easier to convert raw values from the accelerometer. I found this accelerometer to be more sensitive and than the one in the 101.
This iteration of the code originally checked if the accelerometer position was close to 0 on all axes (shell is down on table) or not (shell is picked up) and output the orientation as an integer 0 or 1 respectively. I later slightly adjusted the values to look for when I installed it into the enclosure. The final iteration saves the initial axes position of the accelerometer and checks for change from those values. 
```c
// this is in setup function
// get initial accelerometer position
  initx = acc.getGX();
  inity = acc.getGY();
  initz = acc.getGZ();
```
```c
// this is in loop function
// read accelerometer:
  float x = acc.getGX();
  float y = acc.getGY();
  float z = acc.getGZ();
  
  // board facing up
  if(abs(x - initx) <= 0.35 && abs(y - inity) <= 0.35 && abs(z - initz) <= 0.35 && x < 0 && y < 0 && z < 0){
    orientation = 0;
  }
  // board not facing up
  else{
    orientation = 1;
  }
```

I followed the wiring layout in the [Adafruit tutorial](https://learn.adafruit.com/adafruit-analog-accelerometer-breakouts/wiring){:target="_blank"}:
![alt text](https://cdn-learn.adafruit.com/assets/assets/000/002/497/large1024/sensors_AccelerometerRef_bb-1024.jpg?1396783813)

#### Sound ####
My final iteration uses the [Adafruit VS1053 MP3/AAC/Ogg/MIDI/WAV Codec Breakout Board](https://learn.adafruit.com/adafruit-vs1053-mp3-aac-ogg-midi-wav-play-and-record-codec-tutorial/overview){:target="_blank"}. This made it easy to load and stop multiple tracks as well as control volume.

I followed [Adafruit's wiring guide](https://learn.adafruit.com/adafruit-vs1053-mp3-aac-ogg-midi-wav-play-and-record-codec-tutorial/simple-audio-player-wiring){:target="_blank"} except I connected a speaker to the left output pin LOUT and ground AGND instead of a headphone jack using both channels. My audio files are mono so this works out. The below photo has both sound breakout board and accelerometer connected to the Uno.
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/midterm/wiring_photo.jpg)

I wanted each time a user picked up the shell to be its own experience. In this way, I planned to make the track reveal something if the user listened long enough. My code reflects that. Everytime the user picks up the shell, it plays one track (alternating between 2 tracks, however I could add more). While the user has the shell picked up, the track that's playing will loop until it's put down. And of course, I do not play music if the shell is not picked up. I am using Adafruit VS1053 library's [FilePlayer class](https://learn.adafruit.com/adafruit-vs1053-mp3-aac-ogg-midi-wav-play-and-record-codec-tutorial/library-reference){:target="_blank"} in the code below, which I adapted from the included examples:

```c
 // if not up orientation, play music
    if(orientation != 0 && orientation != -1){
      // alternate tracks when user just picks up shell
      if(lastOrientation != orientation){
         if(justPlayedTrackOne == true){
            musicPlayer.startPlayingFile("track002.mp3");
            justPlayedTrackOne = false;
        }
        else{
          musicPlayer.startPlayingFile("track001.mp3");
          justPlayedTrackOne = true;
        }
      }
      // loop track if shell is still not in up orientation when track finishes (user is still listening)
      else{
        if(musicPlayer.stopped() && justPlayedTrackOne == true){
            musicPlayer.startPlayingFile("track001.mp3");
        }
        else if(musicPlayer.stopped() && justPlayedTrackOne == false){
          musicPlayer.startPlayingFile("track002.mp3");
        }
      }
    }
    else{
      musicPlayer.stopPlaying(); //stop player
    }
```
The audio files were created using Adobe Audition and exported as wav files and then converted to mp3 to work with the tutorial. I had trouble getting my program to recognize the files in the SD card unless they were named 'track001.mp3' or 'track002.mp3' but the library documentation suggests that the names can be anything as long as it's reflected in your code.
I used wave sounds from the [visualization video](https://youtu.be/HppcuRuBz6M){:target="_blank"} to bookend a song in each track. The songs used were [d e c i s i v e d r e a m s by HAUNTXR](https://soundcloud.com/hauntxr/decisive-dreams){:target="_blank"} and [Shi no Aphrodite: Tsuioku](https://youtu.be/50xokvoeEm8){:target="_blank"}.

Mixed tracks used in piece:
<audio src="https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/midterm/shellSoundMusic1-Hauntxr.mp3" controls preload></audio>

<audio src="https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/midterm/shellSoundMusic2-Utena.mp3" controls preload></audio>

#### Screen Visualization ####
The visualization receives data from the Uno from the [p5serial.js library](https://github.com/vanevery/p5.serialport){:target="_blank"}. The p5 sketch receives the orientation (0 or 1) from the Arduino code and hides and unhides the div the video player is in. I am manipulating the DOM using the [p5.dom library](https://p5js.org/reference/#/libraries/p5.dom){:target="_blank"}.
```javascript
if (orientation == 0 && lastOrientation != 0) {
    oceanVideo.hide();
  }
  // isnt up was up
  else if(orientation != 0 && lastOrientation == 0){
    oceanVideo.show();
  }
  lastOrientation = orientation;
```

The video player is simply a YouTube player created using [YouTube's IFrame Player API](https://developers.google.com/youtube/iframe_api_reference){:target="_blank"} with these parameters passed in:
```javascript
      var player;
      function onYouTubeIframeAPIReady() {
        player= new YT.Player('video', {
          height: screen.height,
          width: screen.width,
          videoId: 'HppcuRuBz6M',
          playerVars: {
            'loop': 1,
            'autoplay': 1,
            'controls': 0,
            'color': 'white',
            'fs': 0,
            'showinfo': 0
          },
          events: {
            'onReady': onPlayerReady
          }
        });
      }
```

The video used is a [simple shot of waves crashing](https://www.youtube.com/watch?v=HppcuRuBz6M){:target="_blank"} found on YouTube.

I used node to run a server locally. So, when running the piece, the p5 serial server must be running as well as node. To do this, type `p5serial` in terminal. Make sure the Arduino is sending information to serial. Open another tab and navigate to the folder the sketch is in and type `node server.js`. Open a browser page and go to the local server address and the visualization should be running along with the physical components.

#### Enclosure ####
The shell enclosure is the central point of the piece. In my prototype, the 101 board was housed in the shell enclosure since it contained the accelerometer. After switching to a separate accelerometer, I could reduce the amount of chips I had to fit inside the shell. The final iteration's shell contains the accelerometer and the speaker. The accelerometer is taped face up to a strip of cardboard which is hotglued to the inside. It does not have to be perfectly parallel to the table surface since the code logic is based off of the initial position of the accelerometer. The speaker is also hot glued to the shell. 
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/midterm/shell_closeup.jpg)

I had to solder longer wires to the speaker in order for the shell to be separate from the Uno and sound breakout boards. For the accelerometer connections, I needed to use male to female jumper wire connectors to connect from the Uno to the pins on the breakout accelerometer. I didn't have jumper wires that were long enough so I cut the short ones I had in half, stripped them, and soldered a longer strand of wire inbetween. I then insulated these points with painters tape. I labeled the wires with tape so that I would know where to connect them on the Uno since they are so long as you can see here:
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/midterm/wiring_photo.jpg)

I twisted the speaker and accelerometer wires together and temporarily housed the Uno and sound breakout board in a sunglasses case. To improve upon this, I would create an actual enclosure for the Uno and sound breakout board with surface mount ports. I would use stranded wire for the accelerometer and speaker wires and have a white encasing similar to a telephone wire. I do like the contrast with the speaker sticking out of the natural shell; however, it would be interesting to experiment with a smaller one that could be hidden inside.

Set up consists of: Arduino Uno and sound breakout board within black case, speaker and accelerometer within shell connected to soundbreakout board and Uno respectively, and Uno connected to laptop running visualization.
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/pcomp/midterm/setup_complete.jpg)

I placed the shell on a mouse pad to cushion it when placing it down. The accelerometer value range for changing the orientation are not wide enough so it changes the orientation a couple times when the shell is being put down or picked up do to rocking against the hard table. The pad fixes this a little bit but further tuning would have to be done in the code.

#### Final Iteration ####

<iframe width="560" height="315" src="https://www.youtube.com/embed/a3UXJjs9Gcw" frameborder="0" gesture="media" allowfullscreen></iframe>
