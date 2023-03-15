# Networking-cheat-sheet


Send a UDP Packet:

```
echo "2" > /dev/udp/127.0.0.1/1234
```



Add a virtual interface for a different subnet with a static IP at the new interface

```
sudo ifconfig enp6s0:1 192.168.111.99/24
```
