# Setting up Boatbod OP25 on RPI3B+
This is a guide for setting up OP25 on an RPI3B+ and listening to that audio on a remote device. It can be very difficult to find this info initially, but the process is actually very simple and straightforward.

## Installing OP25
Clone the project and run ./install.sh.

## Running OP25
In the folder `/op25/op25/gr-op25_repeater/apps`, I created a file called `metro.sh`, and use the following command:
`./rx.py --nocrypt --args "rtl" --gains 'lna:36' -S 960000 -X -q 0-v 1 -2 -V -w -W dns_or_ip_of_host_you_want_to_listen_on -l http:0.0.0.0:8080 -T trunk.csv 2> stderr.2`

The important bits are really the dns or ip of the host you want to listen on, the IP and port you want the web dashboard available on, and the name of the trunk data file.

## Listening on another machine
`vlc.exe --clock-jitter=500 --network-caching=0 --demux=rawaud --rawaud-channels 1 --rawaud-samplerate 8000 udp://@:23456`. It opened VLC and it just worked.
