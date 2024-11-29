
# Entries in this file show the compile time defaults. Local configuration
# should be created by either modifying this file (or a copy of it placed in
# /etc/ if the original file is shipped in /usr/), or by creating "drop-ins" in
# the /etc/systemd/resolved.conf.d/ directory. The latter is generally
# recommended. Defaults can be restored by simply deleting the main
# configuration file and all drop-ins located in /etc/.
#
# Use 'systemd-analyze cat-config systemd/resolved.conf' to display the full config.
#
# See resolved.conf(5) for details.

[Resolve]
# Some examples of DNS servers which may be used for DNS= and FallbackDNS=:
# Cloudflare: 1.1.1.1#cloudflare-dns.com 1.0.0.1#cloudflare-dns.com 2606:4700:4700::1111#cloudflare-dns.com 2606:4700:4700::1001#cloudflare-dns>
# Google:     8.8.8.8#dns.google 8.8.4.4#dns.google 2001:4860:4860::8888#dns.google 2001:4860:4860::8844#dns.google
# Quad9:      9.9.9.9#dns.quad9.net 149.112.112.112#dns.quad9.net 2620:fe::fe#dns.quad9.net 2620:fe::9#dns.quad9.net
DNS=8.8.8.8 8.8.4.4
FallbackDNS=1.1.1.1#cloudflare-dns.com 9.9.9.9#dns.quad9.net 8.8.8.8#dns.google 2606:4700:4700::1111#cloudflare-dns.com 2620:fe::9#dns.quad9.n>
#Domains=
#DNSSEC=no
#DNSOverTLS=no
#MulticastDNS=yes
#LLMNR=yes
#Cache=yes
#CacheFromLocalhost=no
#DNSStubListener=yes
#DNSStubListenerExtra=
#ReadEtcHosts=yes
#ResolveUnicastSingleLabel=no
#StaleRetentionSec=0



sudo systemctl restart systemd-resolved


Changed to DeepBlue Network.

[user@bpir3 ~]$ sudo pacman -Syu
[sudo] password for user: 
:: Synchronizing package databases...
 ericwoud                                                   10.7 KiB  2.11 KiB/s 00:05 [##################################################] 100%
 core.db failed to download
error: failed retrieving file 'core.db' from mirror.archlinuxarm.org : Failed to connect to fl.us.mirror.archlinuxarm.org port 80 after 10000 ms: Timeout was reached
error: failed to synchronize all databases (download library error)
[user@bpir3 ~]$ sudo pacman -Syu
:: Synchronizing package databases...
 ericwoud is up to date
 core.db failed to download
error: failed retrieving file 'core.db' from mirror.archlinuxarm.org : Failed to connect to fl.us.mirror.archlinuxarm.org port 80 after 10000 ms: Timeout was reached
error: failed to synchronize all databases (download library error)
[user@bpir3 ~]$ 

Change geo location repository server to specific region ,


(130/130) checking for file conflicts                                                  [##################################################] 100%
(131/131) checking available disk space                                                [##################################################] 100%
warning: could not get file information for etc/hostapd/hostapd.accept
warning: could not get file information for etc/hostapd/hostapd.conf
warning: could not get file information for etc/hostapd/hostapd.deny
warning: could not get file information for etc/hostapd/hostapd.eap_user
warning: could not get file information for etc/hostapd/hostapd.radius_clients
warning: could not get file information for etc/hostapd/hostapd.vlan
warning: could not get file information for etc/hostapd/hostapd.wpa_psk


