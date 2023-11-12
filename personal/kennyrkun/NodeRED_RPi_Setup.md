# Setting up NodeRED on a Raspberry Pi.

1. Install NodeRED from the script.
   - https://nodered.org/docs/getting-started/raspberrypi#running-as-a-service
3. Install Mosquitto MQTT broker.
   - `sudo apt install mosquitto mosquitto-clients`
   - run `sudo systemctl enable mosquitto.service` to enable the service
   - edit `/etc/mosquitto/mosquitto.conf`
   - add the following to lines to the bottom of the file
     - `listener 1883`
     - `allow_anonymous true`
   - restart the broker `sudo systemctl restart mosquitto`
   - run `sudo mosquitto_passwd -c /etc/mosquitto/passwd YOUR_USERNAME`
   - edit `/etc/mosquitto/mosquitto.conf`
   - remove the previous two added lines
   - add `per_listener_settings true` to the top of the file
   - add to bottom of the file
     - `allow_anonymous false`
     - `listener 1883`
     - `password_file /etc/mosquitto/passwd`
   - restart the broker `sudo systemctl restart mosquitto`
