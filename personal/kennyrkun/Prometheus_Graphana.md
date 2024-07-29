The contents of this website are stored here for security: https://medium.com/@austinjayers/how-to-visualize-network-traffic-on-mikrotik-routers-737d67f5e4a8

If you stumbled on this article, it is likely because you want to visualize your network traffic in real-time but “The Dude” isn’t quite working out. No worries! I was in your shoes before, so, let’s get this working the proper way!

Requirements:
A MikroTik Router
A VM or VPS running Ubuntu 20.04 or 22.04
SNMP Enabled on your router

For example, we will pretend the router is on 192.168.0.1 and our VM/VPS is on 192.168.0.2 just for the sake of this tutorial.

    Notice: If you need static IP address blocks, my company CoreTransit can establish a tunnel from our data center to your premises over a GRE connection and provide you with affordable IP blocks! Visit https://coretransit.net for more information!

Installing The Operating System

When installing Ubuntu, ensure you have reasonable resources. I suggest between 4GB and 8GB of RAM, and 100GB of storage. This is just because I want to log trends for all my traffic. You can adjust this accordingly! Also, ensure you set a static IP for your VM/VPS. In this tutorial, we will set 192.168.0.2
Finally, when doing the OS install, create the username “mikrotik”. If you don’t do this, that is okay! Just continue and boot up into the console, and log in.

Execute these commands to create a user called “mikrotik”

sudo adduser mikrotik

Then, set the password. Finally, give sudo permission to the user by executing:

sudo adduser mikrotik sudo

Finally, change into the user

su mikrotik

Now, get into the home directory

cd

Installing Prometheus

sudo apt installupdate
wget https://github.com/prometheus/prometheus/releases/download/v2.41.0/prometheus-2.41.0.linux-amd64.tar.gz
tar -xvf prometheus-2.41.0.linux-amd64.tar.gz
sudo mkdir -p /data /etc/prometheus
cd prometheus-2.41.0.linux-amd64
sudo mv prometheus promtool /usr/local/bin/
sudo mv prometheus.yml /etc/prometheus/prometheus.yml
sudo chown -R mikrotik:mikrotik /etc/prometheus/ /data/
cd
prometheus --version

After executing the final command, you should be prompted with an installed version. Now we need to enable it as a service so it will start on boot up.

sudo nano /etc/systemd/system/prometheus.service

Paste the following into the file

[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

StartLimitIntervalSec=500
StartLimitBurst=5

[Service]
User=mikrotik
Group=mikrotik
Type=simple
Restart=on-failure
RestartSec=5s
ExecStart=/usr/local/bin/prometheus \
  --config.file=/etc/prometheus/prometheus.yml \
  --storage.tsdb.path=/data \
  --web.console.templates=/etc/prometheus/consoles \
  --web.console.libraries=/etc/prometheus/console_libraries \
  --web.listen-address=0.0.0.0:9090 \
  --web.enable-lifecycle

[Install]
WantedBy=multi-user.target

Now you will finalize the Prometheus installation

sudo systemctl enable prometheus
sudo systemctl start prometheus
sudo systemctl status prometheus

You may know press Ctrl+C to close out of the status view

Installing Node Exporter

Node Exporter will help you view the health of your VM/VPS while running Grafana and Prometheus

wget https://github.com/prometheus/node_exporter/releases/download/v1.5.0/node_exporter-1.5.0.linux-amd64.tar.gz
tar -xvf node_exporter-1.5.0.linux-amd64.tar.gz

You will need to move the exporter file to the /usr/local/bin directory

sudo mv \
  node_exporter-1.5.0.linux-amd64/node_exporter \
  /usr/local/bin/

Followed by:

rm -rf node_exporter*
node_exporter --version

You should now see the current installed version, meaning you can press Ctrl+C to close out again.

Time to create the service file!

sudo nano /etc/systemd/system/node_exporter.service

Paste the following text

[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

StartLimitIntervalSec=500
StartLimitBurst=5

[Service]
User=mikrotik
Group=mikrotik
Type=simple
Restart=on-failure
RestartSec=5s
ExecStart=/usr/local/bin/node_exporter \
    --collector.logind

[Install]
WantedBy=multi-user.target

And to activate the service

sudo systemctl enable node_exporter
sudo systemctl start node_exporter
sudo systemctl status node_exporter

To close out of the status, you can press Ctrl+C.

We now need to add the “job” to Prometheus to connect it to the graphing software. Formatting is important!

sudo nano /etc/prometheus/prometheus.yml

At the very end of your prometheus.yml file, you will add this job in for the Node Exporter

  - job_name: node_export
    static_configs:
      - targets: ["localhost:9100"]

Ensure all the correct spacing is kept.

We will now verify the file

promtool check config /etc/prometheus/prometheus.yml

And if it comes back good, we verify with

curl -X POST http://localhost:9090/-/reload

Installing Grafana

Now we install Grafana, the main dashboard software!

sudo apt-get install -y apt-transport-https software-properties-common
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
sudo apt-get update
sudo apt-get -y install grafana
sudo systemctl enable grafana-server
sudo systemctl start grafana-server
sudo systemctl status grafana-server

As long as you see the green “active” status, you can press Ctrl+C and close.

Now, you can visit your assigned IP, in this case, it is http://192.168.0.2:3000 and you will log in with the username admin and the password admin

Now, we will connect Grafana and Prometheus!

sudo nano /etc/grafana/provisioning/datasources/datasources.yaml

Paste the following text

apiVersion: 1

datasources:
  - name: Prometheus
    type: prometheus
    url: http://localhost:9090
    isDefault: true

And now we restart Grafana!

sudo systemctl restart grafana-server

Installing SNMP Exporter

Now, we have to install the SNMP Exporter which will get your MikroTik status!

wget https://github.com/prometheus/snmp_exporter/releases/download/v0.21.0/snmp_exporter-0.21.0.linux-amd64.tar.gz

tar xzf snmp_exporter-0.21.0.linux-amd64.tar.gz

cd snmp_exporter-0.21.0.linux-amd64
ls -lh
sudo cp ./snmp_exporter /usr/local/bin/snmp_exporter
sudo cp ./snmp.yml /usr/local/bin/snmp.yml
cd /usr/local/bin/

We will create the automatic service file again

sudo nano /etc/systemd/system/snmp-exporter.service

You can paste the following text

[Unit]
Description=Prometheus SNMP Exporter Service
After=network.target

[Service]
Type=simple
User=mikrotik
Group=mikrotik
ExecStart=/usr/local/bin/snmp_exporter --config.file="/usr/local/bin/snmp.yml"

[Install]
WantedBy=multi-user.target

Now we will start the service

systemctl daemon-reload
sudo service snmp-exporter start
sudo service snmp-exporter status

As long as you see the green “active:” like before, you can press Ctrl+C and close out of it.

Now, the final step is to add it as a job to Prometheus!

sudo nano /etc/prometheus/prometheus.yml

At the very end, below the Node Exporter I had you paste earlier, paste this. Please note — we are using 192.168.0.1 for the Router IP. You should put your router IP here (whether remote or LAN)

...
  - job_name: snmp
    metrics_path: /snmp
    params:
      module: [if_mib]
    static_configs:
      - targets:
        - 192.168.0.1
    relabel_configs:
      - source_labels: [__address__]
        target_label: __param_target
      - source_labels: [__param_target]
        target_label: instance
      - target_label: __address__
        replacement: localhost:9116  # URL as shown on the UI

We will check the status

promtool check config /etc/prometheus/prometheus.yml

As long as it comes back OK, we can restart Prometheus

sudo service prometheus restart
sudo service prometheus status

If it is all green, you can press Ctrl+C.

Finally, execute the firewall command

sudo ufw disable

Now, we are done on the VPS. You can navigate your browser to your VM/VPS IP which will be where you signed in with the admin/admin permissions. On the left, hover over the 4 squares icon (Dashboards) and select “Import” Type in the ID 14420 and select the data source as Prometheus when asked at the bottom. Select import and now, you can head to “Dashboards” and select “Mikrotik monitoring”.

Now, you will not see any traffic flowing. We need to enable SNMP on your router! Open up WinBox and execute these commands in terminal:

snmp set enabled=yes
snmp community print

You should see the “public” community, but, you will see “Addresses” as ::0

We want to ensure your SNMP is private, so on WinBox, click on “IP” then “SNMP”

Next, open the “Communities” tab and double-click on “public”

Here, set the “Addresses” field to your VM/VPS IP. In this tutorial, it is 192.168.0.2

This ensures no one is watching your data without your permission!

Finally, you can navigate back to your Grafana install (http://192.168.0.2:3000) and select your “Mikrotik monitoring” dashboard.

On the top right, you should change it to “Last 5 Minutes” and “10s” to the right. This will give you the quickest updates!

Now, you should have SNMP traffic flowing to your dashboard, which you can fully expand and enjoy!
