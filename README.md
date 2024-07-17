# Networking-cheat-sheet


# Send a UDP Packet

```
echo "2" > /dev/udp/127.0.0.1/1234
```

## Set a static IP address for an interface:

```
sudo ifconfig eth1 192.168.2.100 up
```

## Add another static IP to your machine on a different subnet
Add a virtual interface for a different subnet with a static IP at the new interface

```
sudo ifconfig enp6s0:1 192.168.111.99/24
```

## Port forward to view web page on remote server
Port forward through an ssh tunnel to another machine on the remote network. e.g. A PC at a coffee shop sshing to a raspberry-pi at home and access an IP camera on the home network.

* `9999` - Port on the PC
* `80` - Port on the camera
* `localhost` - local PC, your browser will go to `localhost:9999`

```bash
ssh -v -N -L \
localhost:9999:camera-ip-address:80 \
pi-user@pi-ip-address
```

## Port forward to view a camera stream

Port forward the RTSP Port:
```bash
ssh -v -N -L \
localhost:8888:camera-ip-address:554 \
pi-user@pi-ip-address
```

Play on the local machine. Use `rtspt` (not `rtsp`) to force the packets to come via tcp on the same port.

```bash
gst-play-1.0 rtspt://camera-user:camera-password@localhost:8888/Streaming/Channels/102
```


# Find machines on a network (can be different subnet)

```bash
nmap -n -sn 192.168.250.0/24
```
or same subnet:

```bash
sudo arp-scan --localnet
```
