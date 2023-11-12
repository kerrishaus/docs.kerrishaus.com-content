# Setting up NodeRED on a Raspberry Pi.

1. Install NodeRED from the script.
   - https://nodered.org/docs/getting-started/raspberrypi#running-as-a-service
2. Install Mosquitto MQTT broker.
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
3. Install zigbee2mqtt
   - You can follow the install guide [here](https://www.zigbee2mqtt.io/guide/installation/01_linux.html#installing).
   - It may be a good idea to follow the instruction for disabling file log output.
4. Once installed, install [node-red-contrib-zigbee2mqtt](https://flows.nodered.org/node/node-red-contrib-zigbee2mqtt)

Now that you've got the basics setup, it's time to configure NodeRED.

1. Add a Zigbee2mqtt Bridge item, and configure the details you setup for your mqtt broker.
2. Pair any devices in the Zigbee2mqtt frontend. By default, it runs on port 8080 on localhost.
