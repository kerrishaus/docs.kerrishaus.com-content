# General
Like the Anytone 878, certain key functions cannot be be bound to a long press and must be bound to a short press even though tough the function itself will activate with a long press. Additionally, when bound to a short press, they disable the ability to assign a different function to the long press. These features are:
- Emergency Alarm

The 578 measurements are approximately: 7.4" faceplate to fan, 1.6' tall, and 5.55' across the faceplate.

# Power Usage
Using a red 7 function digital multimeter set to 5A, power measurements were as follows.
- Idle, not receiving, screen on: 0.48A ~6W
- Receiving (single VFO) analog and playing it at full volume: 0.5A ~6W

| Power         | Digital       | Analog        |
| ------------- | ------------- | ------------- |
|Low            |1.16A ~15W     |1.56A ~20W     |
|Medium         |2.26A ~30W     |3.15A ~40W     |
|High           |3.16A ~40W     |5.84A ~70W     |
|Turbo          |3.92A ~50W     |6.57A ~80W     |

The screen cannot be turned off, neither automatically nor manually. There is however an option to automatically turn the radio off, either after a fixed period of time after power-on or after a fixed period of inactivity. Screen brightness can not be automatically changed, only manually in the settings menu (or in the CPS).

# Remote Head Mounting
The 578 does not support remote head mounting. AnyTone offers a remote speaker/mic unit with a screen and battery which can be connected to the 578 either by Bluetooth or a cable. There is a community made kit designed to relocate the 578's faceplate, although there are some issues with the kit on the Plus model. [AnyTone 578 remote head kit](https://blaydefab.com/index.php/product/anytone-578-faceplate-relocation-kit/).

# BT-01 Accessory
- When in Bluetooth mode, the speaker on the RF deck cannot be used; only the speaker on the handset is available. In cabled mode, either or both speakers can be used.
- In cabled mode, Bluetooth settings are not available. Bluetooth can be enabled on the RF deck and then you can choose either BT or Cable mode when connecting.
- The RF deck can be configured to turn off and on when the BT-01 is turned off and on, however, the BT-01 does not automatically turn on when the RF deck turns on. (Despite being able to detect when the radio is powered on, grrr)
- Repeater Mode cannot be bound to a BT-01 hotkey.

# Handheld Speaker Mic
- The up and down buttons on the handheld speaker mic change the channel in the current zone up or down. The up and down buttons do not function if the microphone is unlocked. The functions of the up and down buttons cannot be reprogrammed.
- The A/B rubber bits at the top of the speaker mic will illuminate for the corresponding VFO that is being transmitted on. The A/B rubber bits the left under the A/B sub channel button are constantly illuminated based on the current primary VFO. The lights on the speaker mic are very dim and virtually non-existent in sunlight.
- The speaker in the speaker mic is very quiet.

# Airband Receive
- Only one airband channel can be received at a time.
- AM Squelch can be set in Settings > Radio Set > Other Func > AM Sq Level on the radio or Optional Setting > AM/FM in the CPS.

# Notes
## TDMA Adaptive
Channels with TDMA Adaptive will receive on both timeslot 1 and timeslot 2. The equivalent feature on the 878 is "Slot suit."

## SWR on through glass antenna
Using a NanoVNA H4 running 4.3, I measured the following SWR on a Tram 1192 mounted on the top of a tinted sunroof:

|Freq (mhz)  |SWR    |
|------------|-------|
|149.2       |2.357  |
|151.9 (MURS)|1.450  |
|153.0 (MURS)|1.24   |
|157.8       |1.974  |
|460.8       |1.331  |
|477.0       |1.138  |
|442.8       |1.066  |
|430.2       |1.34   |
|452.4       |2.11   |
|462.6 (GMRS)|1.427  |
|467.4 (GMRS)| 2.029 |
|469.2       |2.077  |

## Cross-band repeat
Although the 578 will capture and repeat a digital signal using two analog channels, it will not be usable, even at the correct bandwidth. You can however repeat DMR into analog voice or analog voice into DMR by setting each channel to the appropriate type. You cannot use the A+D or D+A channel types in repeater mode.

Notes:
- Repeater mode persists through restarts.
