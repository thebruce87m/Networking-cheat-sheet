# Networking-cheat-sheet


Send a UDP Packet:

```
echo "2" > /dev/udp/127.0.0.1/1234
```



Add a virtual interface for a different subnet with a static IP at the new interface

```
sudo ifconfig enp6s0:1 192.168.111.99/24
```


Port forward through an ssh tunnel to another machine on the remote network. e.g. A PC at a coffee shop sshing to a raspberry-pi at home and access an IP camera on the home network.

* `9999` - Port on the PC
* `80` - Port on the camera
* `localhost` - local PC, your browser will go to `localhost:9999`

```bash
ssh -v -N -L \
localhost:9999:camera-ip-address:80 \
pi-user@pi-ip-address
```
