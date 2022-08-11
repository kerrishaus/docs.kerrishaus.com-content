# Bluetooth Audio

Typically, when I'm out and about with my boys either on foot or in a vehicle, we use either phones or analog radios to communicate. In general, this works fine. But there are some big disadvantages to both cases, and so I'd like to develop a solution that covers most of (if not even all) of the drawbacks to using these devices.

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
- https://www.sparkfun.com/products/retired/11927
- https://www.sparkfun.com/products/14923 (bluetooth IoT SoC ?)
- https://www.sparkfun.com/products/19475 (supports Apple iAP but is very expensive)

# nRF52840

The nRF52840 is a small and powerful Bluetooth module from Nordic Semiconductor. SparkFun has a wonderful looking development board for this chip.

https://www.sparkfun.com/products/15025

Though I can't tell if this is well suited for audio.

# Other resources
- https://www.youtube.com/watch?v=afGxMfy7_0A
- http://educ8s.tv/arduino-two-way-bluetooth-communication/
- https://howtomechatronics.com/tutorials/arduino/arduino-and-hc-05-bluetooth-module-tutorial/
- https://forum.arduino.cc/t/how-would-i-use-a-rn-52-module-to-play-music-from-my-iphone-to-my-car/549872/5
- https://learn.sparkfun.com/tutorials/understanding-the-bc127-bluetooth-module
