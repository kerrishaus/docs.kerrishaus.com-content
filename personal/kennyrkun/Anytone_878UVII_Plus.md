# AnyTone 878UVII+
General notes
- Dual VFO, single transceiver.
- When being used with a main channel and a sub-channel which are both analog or both digital, if either channel is receiving you will not be able to transmit on the opposite channel until the radio stops receiving. This can be rather irritating on some high-traffic channels.
  - For example, using weather alert renders any 2nd channel unusable.
  - You cannot speak on a 2nd channel if someone is speaking on the first.

## Accessories
- Kenwood SMKW1002 swivel belt clip can be screwed into the battery without modification.
- BaofengTech BTECH-K1 APRS cable is compatible and works with this radio.
- The radio will pair to AirPods with bluetooth.

## Radio Settings
System-wide settings

### Key Settings
Like the Anytone 578, certian key functions cannot be be bound to a long press and must be bound to a short press even though tough the function itself will activate with a long press. Additionally, when bound to a short press, they disable the ability to assign a different function to the long press. These features are:
- Emergency Alarm

### Tone Scanning
This radio has the ability to detect the currently used CTCSS/DCS tone from received transmission.
1. Bind a programmable key to "CDT Scan"
2. Tune to the frequency/channel
  - The frequency/channel you want to use must have a CDT tone set. It doesn't matter which one, it just has to be active. If no tone is set, you will see an "Rx CDT Not Open!" error.
4. Press the key you bound to CDT Scan and the display will slowly scan through all the CDT codes for whichever type you've specified. This process is painfully slow.
5. Begin transmitting on the device that you want to find the CDT tone of, and continue transmitting until the code is found.

## Channel Settings
Settings for individual channels

### Analog APRS
#### Receiving
"APRS Receive" setting options do the following:
- off: will play any received audio including APRS data, will not decode or display information
- on: decodes and displays any received APRS packets, you can hear the audio.
- on (mute): decodes and displays any received APRS packets. while this is on, all audio on the selected frequency is muted.

Any APRS messages received on any channel will go into the APRS inbox in the menu, and can be retreived and viewed at any time.

#### APRS Messaging
This radio supports analog APRS messaging, which is very similar to DMR's SMS. You enter your destination callsign, then your message, and it is sent as an APRS packet. If the receiving radio is listening to an APRS channel, they will receive the message. Unfortunately, the radio does not have any smart features like reply or forward for messages. Instead, to reply you will have to enter the callsign and message of the receipient radio. The radios also have no notification for messages received via APRS, so you will have to check manually to see if they have been received.

### Radio ID
Radio ID is the ID used for DMR. It is usually assigned by the DMR-MARC group via [radioid.net]. This ID is associated with your amatuer radio callsign, but does not pre-empt you from the requirement of identifiying. Typically you will still be expected to identify by voice in a DMR transmission. A valid DMR ID is often required by repeaters or infrastructure groups, like Brandmeister. However, an assigned DMR ID is not necessary to use DMR in general. You can enter any ID you like, as long as everybody around you agrees to you using it.
- Radio ID cannot be entered in the radio, it must be set in the CPS. However, when multiple radio IDs are stored in the radio, you can choose which one to use at any time.
- Radio ID is set per channel, not radio wide. Channels can have different Radio IDs set in codeplug, or manually on the radio. There is no way to apply a Radio ID to every channel automatically.
