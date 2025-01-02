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

> ip neighbour is not ok, duplication ခနခနဖြစ်ပြီး၊ bind ထားတဲ့ mac address နဲ့ ip address နဲ့ မကျရောက်။

```
[user@bpir3 ~]$ systemctl --version
systemd 255 (255.4-2-arch)
+PAM +AUDIT -SELINUX -APPARMOR -IMA +SMACK +SECCOMP +GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN +IPTC +KMOD +LIBCRYPTSETUP 
+LIBFDISK +PCRE2 +PWQUALITY +P11KIT +QRENCODE +TPM2 +BZIP2 +LZ4 +XZ +ZLIB +ZSTD +BPF_FRAMEWORK +XKBCOMMON +UTMP -SYSVINIT default-hierarchy=unified
[user@bpir3 ~]$ 
```

### More Option From 

https://www.freedesktop.org/software/systemd/man/latest/systemd.network.html#%5BDHCPServerStaticLease%5D%20Section%20Options

```
[DHCPServerStaticLease] Section Options
The "[DHCPServerStaticLease]" section configures a static DHCP lease to assign a fixed IPv4 address to a specific device based on its MAC address. This section can be specified multiple times.

MACAddress=
The hardware address of a device to match. This key is mandatory.

Added in version 249.

Address=
The IPv4 address that should be assigned to the device that was matched with MACAddress=. This key is mandatory.

Added in version 249.

```

### Config for 10-brlan.network

```
[Match]
Name=brlan

[Network]
Address=192.168.1.100/24
IPForward=yes
DHCPServer=yes

[DHCPServer]
EmitDNS=yes
DNS=8.8.8.8

[DHCPServerStaticLease]
MACAddress=aa:bb:cc:dd:ee:ff
Address=192.168.5.100

[DHCPServerStaticLease]
MACAddress=11:22:33:44:55:66
Address=192.168.5.101
```

[DHCPServerStaticLease]
MACAddress=d4:6a:6a:c8:fd:4d
Address=192.168.1.120

http://linux-ip.net/html/tools-ip-neighbor.html


The `PoolOffset` and `PoolSize` options in the `[DHCPServer]` section of your `.network` file control the range of dynamically allocated IP addresses within your subnet. Here's how they work:

### **Key Options**
1. **`PoolOffset`**:
   - Specifies the offset from the network address at which the dynamic pool starts.
   - For example, in a subnet `192.168.5.0/24`:
     - `PoolOffset=100` starts the pool at `192.168.5.100`.

2. **`PoolSize`**:
   - Defines the number of IP addresses available in the pool.
   - For example:
     - If `PoolOffset=100` and `PoolSize=50`, the range is `192.168.5.100` to `192.168.5.149`.

3. **Dynamic Range**:
   - The DHCP server will dynamically assign IP addresses in the range `192.168.5.100` to `192.168.5.149`.
   
4. **Static Addresses**:
   - Devices with the specified MAC addresses will get `192.168.5.10` and `192.168.5.20`.

5. **Non-overlapping**:
   - Ensure that static addresses (`192.168.5.10`, `192.168.5.20`) do not overlap with the dynamic range (`192.168.5.100`–`192.168.5.149`).

### Restart to Apply Changes

```bash
sudo systemctl restart systemd-networkd
```

### Change Date & TIME ZONE (auto sync)
```
[root@bpir3 user]# sudo timedatectl set-timezone Asia/Yangon
```
```
[root@bpir3 user]# date
Thu Jan  2 17:03:36 +0630 2025
```
```
[root@bpir3 user]# timedatectl
               Local time: Thu 2025-01-02 17:03:46 +0630
           Universal time: Thu 2025-01-02 10:33:46 UTC
                 RTC time: n/a
                Time zone: Asia/Yangon (+0630, +0630)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no
[root@bpir3 user]# 
```

