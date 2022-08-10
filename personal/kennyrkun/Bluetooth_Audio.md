# Bluetooth Audio

I would like to create a small, simple device to stream bi-directional audio to a smartphone (iPhone specifically, for now). I'm looking to use Arduino or RaspberryPi microcontrollers to accomplish this.

The goal of the project is to stream audio from the phone to a speaker on the device, and stream audio from a microphone back to the phone.

The general consensus that I've found for these goals is: just give up.

Apparently streaming audio just one way through Bluetooth is not a trivial endeavour.

# RN-52

I've found a few good leads in the right direction so far. The most notable being the RN-52 breakout board from Sparkfun. On paper, this board is everything I need. It has a built in bluetooth module and connections for both a speaker and a microphone, and is setup for audio streaming out of the box. Unfortunately, the reviews for the board are very negative regarding it's audio quality for microphones, which is not good for us.

RN-52 Related Links
- https://www.sparkfun.com/products/retired/12849
- https://learn.sparkfun.com/tutorials/rn-52-bluetooth-hookup-guide/all
- https://cdn.sparkfun.com/assets/a/2/a/a/d/5217c61f757b7f55758b456f.pdf
- http://www.jenrathbun.com/Electronics/rn52-bluetooth-adapter-microphone/

Similar products:
- https://www.sparkfun.com/products/retired/11927
- https://www.sparkfun.com/products/14923 (bluetooth IoT SoC ?)

# nRF52840

The nRF52840 is a small and powerful Bluetooth module from Nordic Semiconductor. SparkFun has a wonderful looking development board for this chip.

https://www.sparkfun.com/products/15025