# Setting up Boatbod OP25 on RPI3B+
This is a guide for setting up OP25 on an RPI3B+ and listening to that audio on a remote device. It can be very difficult to find this info initially, but the process is actually very simple and straightforward.

## Installing OP25
Clone the project and run ./install.sh.

## Running OP25
In the folder `/op25/op25/gr-op25_repeater/apps`, I create a bash script with the following commands
`./rx.py --n --args "rtl" --gains 'lna:36' -S 960000 -X -q 0-v 1 -2 -V -w -W dns_or_ip_of_host_you_want_to_listen_on -l http:ip_dash_board_is_reachable_at:8080 -T trunk.csv`

The argument `-l` specifies the address the webserver will listen on. To use the web interface from anywhere within the same network, use the local address of the device running OP25. To access the interface from outside of the local network, I recommend Nginx Proxy Manager with scheme of HTTP, SSL Forced, and an Access List. If you don't want to the web interface available anywhere other than the local device, use 0.0.0.0.

The argument `-w` enables Wireshark packet sharing. It usually requires argument `-W` to be provided in combo. The `-W` argument takes an IP address as a variable, this is the IP it will send the frames to. If you want the frames available on the entire network, use multicast address `224.0.0.1`.

- `-v` sets the verbosity of debug messages, with 0 being the least and 9 being the most.
- `-V` enables the vocoder.
- `-U` enabled the build in UDP audio receiver, which plays back to the default audio device.

## Listening with VLC
`vlc.exe --clock-jitter=500 --network-caching=0 --demux=rawaud --rawaud-channels 1 --rawaud-samplerate 8000 udp://@:23456`. It opened VLC and it just worked.
