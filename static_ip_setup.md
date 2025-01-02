## Static IP Configuration in the Ethernet Layer

## using ip neigh to configure ARP permanent entries


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

sudo ip neigh add 192.168.5.140 lladdr <m:a:c:a:d:d:> dev brlan

sudo ip neigh del 192.168.5.146 dev brlan

sudo ip neigh flush dev brlan
```



http://linux-ip.net/html/tools-ip-neighbor.html


