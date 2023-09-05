# Portal for the Raspberry Pi

## Setting up a Kiosk

1. Install Raspbian lite, 64-bit.
2. Create a new user named `kiosk`.
3. Run `sudo apt-get update && sudo apt-get upgrade` to update all preinstalled packages.
4. Install the packages `openbox`, `xserver-xorg`, `xprintidle`, and `chromium-browser`.
5. Clone the [portal-rpi](https://git.kerrishaus.com/portal-rpi) to the kiosk user's home directory.
6. Run `sudo python3 portal.py -install` to install the `portal-gui` and `portal` services.
