# Bluetooth Audio

Typically, when I'm out and about with my boys either on foot or in a vehicle, we use either phones or analog radios to communicate. In general, this works fine. But there are some big disadvantages to both cases, and so I'd like to develop a solution that covers most of (if not even all) of the drawbacks to using these devices.

[__TOC__]

## Pros and Cons of each

### Phone Calls

#### Phone Call Cons
- Sound quality is quite poor
- Difficult to add multiple recipients
- Quick communication is difficult, because recipients must answer calls manually.

#### Phone Call Pros
- Nearly unlimited range
- Very simple

### VoIP software

#### VoIP Pros
- Nearly unlimited range
- Generally good sound quality
- Extensibility, like messages, private calls, specific user muting, music, etc

#### VoIP Cons
- All users are required to download the app and setup an account
- Difficult to quickly communicate with new users

In general, when reading forum posts about bluetooth audio using the typical microcontrollers, there is very little information. Many users are met with hostility and told to give up and find something else to do, which I think is a terrible way to help a newcomer grow. And I'm not giving up.

# RN-52

I've found a few good leads in the right direction so far. The most notable being the RN-52 breakout board from Sparkfun. On paper, this board is everything I need. It has a built in bluetooth module and connections for both a speaker and a microphone, and is setup for audio streaming out of the box. Unfortunately, the reviews for the board are very negative regarding it's audio quality for microphones, which is not good for us. I think this chip is going to be the one I end up going with, and I will pair it with a microcontroller like an Arduino Nano or a Pi Zero.

RN-52 Related Links
- https://www.sparkfun.com/products/retired/12849
- https://learn.sparkfun.com/tutorials/rn-52-bluetooth-hookup-guide/all
- https://cdn.sparkfun.com/assets/a/2/a/a/d/5217c61f757b7f55758b456f.pdf
- http://www.jenrathbun.com/Electronics/rn52-bluetooth-adapter-microphone/

Similar products:
- https://www.sparkfun.com/products/retired/11927 (BC127 break out board, this looks like the ideal chip)
- https://www.sparkfun.com/products/retired/11924 (features the same chip from the above link, but has other goodies)
- https://www.sparkfun.com/products/14923 (bluetooth IoT SoC ?)
- https://www.sparkfun.com/products/19475 (supports Apple iAP but is very expensive)

# nRF52840

The nRF52840 is a small and powerful Bluetooth module from Nordic Semiconductor. SparkFun has a wonderful looking development board for this chip.

https://www.sparkfun.com/products/15025

Though I can't tell if this is well suited for audio.

# BC127

Cedrus Libani / about 8 years ago /  1
I can't figure out how to connect a mic to this. I got the Sparkfun electret microphone breakout and the mems microphone breakout , but the pins don't really match. The mic breakouts have VCC, GND, and AUD, whereas BC127 has MIC_RN, MIC_RP, and MIC_BIAS (and GND) which probably means the BC127 expects balanced audio input? Anyway, with VCC 3.3V, AUD connected to MIC_RP and GND connected to either MIC_RN or to GND, all I get is excruciating noise. Does anybody know this?
Cedrus Libani / about 8 years ago /  1
ok, maybe it was because I used 3v3 from an FTDI basic board to power the mic, because when I used a 1.5v battery it worked much better.
Cedrus Libani / about 8 years ago /  1
Hmm. I still only get good signal when I power the Mic and the BC127 from separate sources. Does anybody know how to hook up a SparkFun MEMS Microphone and the BC127 on a single battery?
Cedrus Libani / about 7 years ago /  2
OK solved it but I did have to upgrade firmware. Connect mic breakout GND to BC127 GND and to MIC-. Connect AUD to MIC+. Connect VCC to MIC_BIAS. Mic is now powered by same battery and there is less noise. MIC_BIAS cannot be set in Melody 5.0. I upgraded to Melody 5.7RC4. MIC_BIAS is set using command 'CODEC'.
pedroserano / about 7 years ago /  1
Thank you so much!!! I was getting horrendous noise on my microphone and your comment solved my problem. In retrospect it was a really stupid mistake, but in case anyone has this same problem, the noise coming across the line of the MIC (and speaker) came from the fact that I connected the mic GND straight to the arduino's GND through the breadboard, when in fact I should have connected it to the BC-127 breakout board GND instead.

You can configure the module to output in mono by adjusting the codec setting. The default codec setting is 0 0 1, with the third digit representing stereo/mono output. If you set that last integer to be zero, then the module will output in mono over the left channel output.

# Summary

- Arduino is not suited for audio processing.
- The bluetooth module must support HSP.

# Other resources
- https://www.youtube.com/watch?v=afGxMfy7_0A
- http://educ8s.tv/arduino-two-way-bluetooth-communication/
- https://howtomechatronics.com/tutorials/arduino/arduino-and-hc-05-bluetooth-module-tutorial/
- https://forum.arduino.cc/t/how-would-i-use-a-rn-52-module-to-play-music-from-my-iphone-to-my-car/549872/5
- https://learn.sparkfun.com/tutorials/understanding-the-bc127-bluetooth-module
- https://www.tinypico.com <-- this guy might be enough to power the project
