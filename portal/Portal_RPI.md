# Portal for the Raspberry Pi

## Setting up a Kiosk

1. Install Raspbian lite, 64-bit.
2. Create a new user named `kiosk`.
3. Run `raspi-config` and set Boot Options > Desktop CLI > Console Autologin.
4. Run `apt-get update && apt-get upgrade` to update all preinstalled packages.

Here you should configure your networking the way you want it. In some cases, it may be beneficial to setup a static IP. However, unless configured otherwise, the client script will automatically report its own local and public address to the Portal Devices server periodicially, keeping it up to date and in sync with any changes that may be caused by dynamic address assignment.  

To set a static IP:
1. Open `/etc/dhcpcd.conf` in your editor of choice.
2. Configure these fields, according to your own needs:
```
interface wlan0
static_routers=192.168.0.1
static domain_name_servers=192.168.0.1 1.1.1.1 8.8.8.8
static ip_address=192.168.0.10/24
```
3. Save the file and reboot or restart the `dhcpcd` service.

5. After networking is configured, enable SSH. (you can then continue setup over SSH)  
6. Install the packages `openbox`, `xserver-xorg`, `xprintidle`, and `chromium-browser`.
7. Clone the [portal-rpi](https://git.kerrishaus.com/portal-rpi) to the kiosk user's home directory.
8. Run `sudo python3 portal.py -install` to install the `portal-gui` and `portal` services.
9. Open `/etc/xdg/openbox/autostart` for editing, and input the following:
```
# Disable any form of screen saver / screen blanking / power management
xset s off
xset s noblank
xset -dpms

# Start Chromium in kiosk mode
sed -i 's/"exited_cleanly":false/"exited_cleanly":true/' ~/.config/chromium/'Local State'
sed -i 's/"exited_cleanly":false/"exited_cleanly":true/; s/"exit_type":"[^"]\+"/"exit_type":"Normal"/' ~/.config/chromium/Default/Preferences
chromium-browser --disable-infobars --check-for-update-interval=31536000 --noerrdialogs --kiosk 'https://portal.kerrishaus.com'
```
10. Now, open `~/.bash_profile` and input the following:
`[[ -z $DISPLAY && $XDG_VTNR -eq 1 ]] && startx -- -nocursor`

That should be all that's required to get up and running.
