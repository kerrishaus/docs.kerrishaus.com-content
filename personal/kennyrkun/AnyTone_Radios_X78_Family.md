# AnyTone X78 Family
This document refers to shared features of the 878 and the 578.

# Radio ID
Radio is the ID used to identify your radio in DMR transmissions. Radio ID is a key part of the DMR standard, and all brands of DMR radio will transmit and decode your radio ID from one radio to another. You can use any number you want as a radio ID; however certain networks such as Brandmeister may require a radio ID assigned by a central body, such as [radioid.net]

 New Radio IDs cannot be set from the front panel, they must be set by the CPS. Once set, you can change the radio ID used by a particular channel in the CPS or from the radio's front panel. For radios running firmware version 3.04 or earlier, the radio ID is set per channel, and cannot be set globally. Firmware version 3.05 and later introduced "Master Radio ID." From the front panel, the master radio ID can be set to one of the radio IDs included in the codeplug, new radio IDs still cannot be added from the front panel. If a channel is set to use the master radio ID, it will automatically be updated when the master radio ID is changed. If a channel is set to use a specific radio ID, it will not be affected by changing the master radio ID.

# Emergency Alarm
The emergency alarm can be activated manually using the alarm key function, or automatically using the "Work Alone" function. It will alternate between transmitting and receiving each for a configurable duration, and the alarm itself has a configurable duration (which cannot be infinite.) Emergency alarm can be configured to always use a particular channel, which can be different based on the mode of the current channel. In digital modes, when transmitting via the emergency alarm, receiving AnyTone radios will display "Alarm" on the call screen, but will not play a special sound or otherwise differentiate the transmission from any other type of call.

# Analog APRS Messaging
Both the 878 and 578 support SMS messages through APRS. You must use the entire callsign including the SSID in order for the radio to receive and decode the message. If the SSID is ommitted, the radios will ignore the message.

# Contacts
A contact with the Ring set to Ring will play the triple beep caller after being heard, and Ring set to Online Alert will play the talk permit tone (if one is set) before playing audio from that contact.
