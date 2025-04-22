# Using Boatbod OP25 on RPI3B+
A compiled guide on setting up and listening to OP25 on a Raspberry Pi 3b+.

## Installing OP25
Clone the project and run ./install.sh. Surprisngly, this usually works without issue.

## Running OP25
In the folder `/op25/op25/gr-op25_repeater/apps`, create a bash script with the following command:
`./rx.py --n --args "rtl" --gains 'lna:36' -S 960000 -X -q 0 -v 1 --phase2-tdma -V -w -W dns_or_ip_of_host_you_want_to_listen_on -l http:ip_dash_board_is_reachable_at:8080 -T system.tsv`

The argument `-l` specifies the address the webserver will listen on. To use the web interface from anywhere within the same network, use the local address of the device running OP25. To access the interface from outside of the local network, I recommend Nginx Proxy Manager with scheme of HTTP, SSL Forced, and an Access List. If you don't want to the web interface available anywhere other than the local device, use 0.0.0.0.

The argument `-w` enables Wireshark packet sharing. It usually requires argument `-W` to be provided in combo. The `-W` argument takes an IP address as a variable, this is the IP it will send the frames to. If you want the frames available on the entire network, use multicast address `224.0.0.1`.

- `-v` sets the verbosity of debug messages, with 0 being the least and 9 being the most.
- `-V` enables the vocoder.
- `-U` enabled the build in UDP audio receiver, which plays back to the default audio device.
- `-d` sets the frequency tuning offset either negative or positive. expect to have to adjust this for maximum audio quality. Mine is set to -1100.

## Run OP25 on startup
```
[Unit]
Description=OP25 Decoder
After=network.target

[Service]
Type=simple
User=sdr
Group=sdr
WorkingDirectory=/home/sdr/op25/op25/gr-op25_repeater/apps
# you have to create the script below. use the command given above.
ExecStart=/home/sdr/op25/op25/gr-op25_repeater/apps/op25.sh

[Install]
WantedBy=multi-user.target
```

## Listening with VLC
`vlc.exe --clock-jitter=500 --network-caching=0 --demux=rawaud --rawaud-channels 1 --rawaud-samplerate 8000 udp://@:23456`. It opened VLC and it just worked.

## Restreaming it with a Discord Bot
1. Setup a loopback audio device:
   - Linux: https://askubuntu.com/questions/1497815/how-to-create-multiple-loopback-cards-using-alsa
     - Put `options snd-aloop index=2` in `/usr/share/alsa/alsa.conf` to retain the loopback device on reboot
2. Setup the bot: https://gist.github.com/kennyrkun/c5ffc136479e9a90a8a1ec0679dd899a based on https://github.com/ygorpontelo/discord_stream_bot/
3. Run OP25 with `--udp-player` enabled and `--audio-output` set to the device that the bot will be listening to.
  
### Run the Discord bot on startup
```
[Unit]
Description=OP25 Restreaming Discord Bot
Requires=op25.service network-online.target
After=op25.service

[Service]
Type=simple
User=sdr
Group=sdr
WorkingDirectory=/home/sdr/op25discord
# delay starting until 10 seconds after OP25 has started, to give it time to set the output sample rate for the loopback device 
ExecStartPre=/bin/sleep 10
ExecStart=python3 /home/sdr/op25discord/bot.py
Restart=always

[Install]
WantedBy=multi-user.target
```
