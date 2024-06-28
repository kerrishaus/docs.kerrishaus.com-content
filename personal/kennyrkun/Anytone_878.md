# AnyTone 878
General notes
- Single VFO single receiver
- When being used with a main channel and a sub-channel which are both analog or both digital, if either channel is receiving you will not be able to transmit on the opposite channel until the radio stops receiving. This can be rather irritating on some high-traffic channels.

## Accessories
- Kenwood SMKW1002 swivel belt clip fits without modification
- BaofengTech BTECH-K1 APRS cable is compatible and works with this radio
- The radio will pair to AirPods with bluetooth.

## Radio Settings
System-wide settings

### Tone Scanning
This radio has the ability to detect the currently used CTCSS/DCS tone from received transmission.
1. Bind a programmable key to "CDT Scan"
2. Tune to the frequency/channel
  - The frequency/channel you want to use must have a CDT tone set. It doesn't matter which one, it just has to be active.
4. Press the key you bound to CDT Scan and the display will slowly scan through all the CDT codes for whichever type you've specified. This process is painfully slow.
5. Begin transmitting on the device that you want to find the CDT tone of, and continue transmitting until the code is found.

## Channel Settings
Settings for individual channels

### Analog APRS
"APRS Receive" setting options do the following:
- off: will play any received audio including APRS data, will not decode or display information
- on: will play any received audio including APRS data, will not decode or display information
- on (mute): displays any received and decoded APRS messages on the display briefly. will not play any audio from the channel this is set on.

### Radio ID
- Radio ID is set per channel, not radio wide. Channels can have different Radio IDs set in codeplug, or manually on the radio. There is no way to apply a Radio ID to every channel automatically.
