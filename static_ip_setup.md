## Static IP Configuration in the Ethernet Layer

## using ip neigh to configure ARP permanent entries

d4:6a:6a:c8:fd:4d 	Dell network adapter laptop 
4e:5a:89:4d:a6:39	mac network adapter

```
iw dev wlan0 station dump
```
```
ip neigh show
```
```
arp -a
```

```
ip neigh show dev brlan

sudo ip neigh add 192.168.5.140 lladdr 4e:5a:89:4d:a6:39 dev brlan

sudo ip neigh del 192.168.5.146 dev brlan

sudo ip neigh flush dev brlan
```



http://linux-ip.net/html/tools-ip-neighbor.html


