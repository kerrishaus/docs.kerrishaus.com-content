# AnyTone X78 Family
This document refers to shared features of the 878 and the 578.

# Radio ID
Radio ID is a number sent along with your transmission that identifies your radio. A radio ID is always required to make a DMR transmission, however there is no central radio ID authority. You can use whatever number you want and make transmissions. However, there are networks that use their own standards for radio IDs (radioid.net, Brandmeister, etc.) To use those systems, you will need to use their radio IDs.

Fortunately, you can store multiple radio IDs in the CPS. Channels can be set to use a particular radio ID from the CPS. New radio IDs cannot be added from the front panel, but you can change which radio ID a particular channel uses from the front panel.

For 878 radios running firmware version 3.04 or earlier, the radio ID is set per channel, and cannot be set globally. Firmware version 3.05 and later introduced "Master ID." The master ID must be set from the CPS. In the CPS, it can be enabled for all channels. Master ID cannot be set per channel in the CPS. From the front panel, master ID can be set per channel.

# Mixed Mode Channels
Mixed mode channels will receive both digital and analog. After receiving a transmission, the radio will transmit in the same mode that was received for the duration of the call hold time for that particular mode. After the hold time, the radio will transmit in the primary mode of the channel. In mixed mode, digital functions such as SMS receive, call alert, radio check, location, remote monitor will work regardless of primary channel type.

# Emergency Alarm
The emergency alarm can be activated manually using the alarm key function, or automatically using the "Work Alone" function. It will alternate between transmitting and receiving each for a configurable duration, and the alarm itself has a configurable duration (which cannot be infinite.) Emergency alarm can be configured to always use a particular channel, which can be different based on the mode of the current channel. In digital modes, when transmitting via the emergency alarm, receiving AnyTone radios will display "Alarm" on the call screen, but will not play a special sound or otherwise differentiate the transmission from any other type of call.

# Analog APRS Messaging
Both the 878 and 578 support SMS messages through APRS. You must use the entire callsign including the SSID (the -7 or whatever) in order for the radio to receive and decode the message. If the SSID is ommitted, the radios will ignore the message.

# Roaming
## DMR Roam / Roaming Zones
Roaming Zones apply only to DMR. Roaming Zones cannot be used for analog channels. Analog channels can be added to Roaming Zones, but shouldn't be because they won't do anything.

## GPS Roaming
Only 16 channels can be used for GPS roaming. GPS roaming channels can be digital or analog. Radius is generally in meters. Roaming toggle can't be set using a hotkey, it must be done manually in a menu. Go to Menu -> GPS -> Area SQL -> On/Off and to turn it on or off. In CPS, it can be enabled by default under Optional Setting -> GPS Ranging -> GPS Roaming.

# Contacts
A contact with `Call Alert` set to `Ring` will play the triple beep caller(what is this?) after being heard, and `Ring` set to `Online Alert` will play the talk permit tone (if one is set) before playing audio from that contact.

# Tips for using the CPS
- For sections that contain lists that don't allow you to use the "Insert (Paste)" or "Move up"/"Move down" actions in the context menu, you can move an item by using control + x or "Cut". Then paste the item where you need it.

# Icons
- Big red letter A: Auto power off indicator. Not shown when Bluetooth is enabled.
- Big letter R: Roaming indicator. Not shown when Bluetooth is enabled.
  - Red: Roaming is enabled and searching
  - Green: Roaming repeater found
- Red speaker: Digital monitor enabled. Will have one volume line if single slot, two monitor lines for double timeslot.
- Blue microphone icon: VOX enabled
- Red square with white microphone in center: Recording enabled
- Location pin/Satellite:
  - Gray: GPS enabled, no lock
  - Red/Green: GPS enabled, locked.
- Red square with black diamond in center above channel name: Encryption enabled on channel
