### **Linux WPA/WPA2/IEEE 802.1X Supplicant (wpa_supplicant) အကြောင်း မြန်မာလိုရှင်းပြချက်**  

**wpa_supplicant** သည် Linux, BSD, Mac OS X, နှင့် Windows များအတွက် **WPA (Wi-Fi Protected Access)** နှင့် **WPA2 (IEEE 802.11i / RSN)** ကို ထောက်ပံ့နိုင်သော **Wi-Fi Client Software (Supplicant)** ဖြစ်သည်။  

#### **wpa_supplicant ဘာလုပ်ပေးနိုင်လဲ?**  
- **Wi-Fi ချိတ်ဆက်မှုကို ထိန်းချုပ်ခြင်း**  
- **WPA/WPA2-PSK (WPA-Personal)** နှင့် **WPA/WPA2-Enterprise** ထောက်ပံ့နိုင်ခြင်း  
- **IEEE 802.1X authentication** (EAP, RADIUS စသည်) ကို ထောက်ပံ့နိုင်ခြင်း  
- **Wi-Fi Security နည်းလမ်းများ (CCMP, TKIP, WEP)** ကို ထောက်ပံ့နိုင်ခြင်း  

#### **wpa_supplicant သည် ဘယ်လို အလုပ်လုပ်သလဲ?**  
wpa_supplicant သည် **daemon** တစ်ခုအဖြစ် နောက်ကွယ်တွင် လည်နေသည်။  
Wi-Fi ချိတ်ဆက်ရန်အတွက် အောက်ပါ အဆင့်များကို လိုက်နာသည် -  

1. **Wi-Fi AP (Access Point) များကို Scan ပြုလုပ်သည်**  
2. **အသုံးပြုမည့် AP ကိုရွေးချယ်သည်**  
3. **ကွန်နက်ရှင်းလုပ်ရန် Kernel driver ကို ချိတ်ဆက်သည်**  
4. **WPA-EAP Authentication လုပ်ဆောင်သည် (Enterprise Mode အတွက်)**  
5. **WPA-PSK Authentication (Personal Mode အတွက်) ကို လုပ်ဆောင်သည်**  
6. **Wi-Fi ချိတ်ဆက်မှု အောင်မြင်ပါက Data Packets ထွက်/ဝင်နိုင်သည်**  

#### **wpa_supplicant ထောက်ပံ့နိုင်သည့် EAP Authentication နည်းလမ်းများ**  
- **EAP-TLS, EAP-PEAP (MSCHAPv2, TLS, GTC, OTP, MD5)**  
- **EAP-TTLS, EAP-SIM, EAP-AKA, EAP-FAST**  
- **EAP-PSK, EAP-IKEv2, LEAP**  

#### **ထောက်ပံ့နိုင်သည့် Driver များ**  
- **Linux Wireless (wext) v19+**  
- **HostAP, madwifi (Atheros), Intel ipw2100/ipw2200**  
- **Broadcom wl, ndiswrapper, FreeBSD net80211**  
- **Windows NDIS driver (XP, 2000)**  

#### **wpa_supplicant Configuration (ဖိုင်ပြင်ဆင်မှု)**  
wpa_supplicant သည် **text-based configuration file** တစ်ခု (wpa_supplicant.conf) ကို အသုံးပြုသည်။  
```ini
network={
    ssid="MyWiFi"
    psk="my_secure_password"
}
```
**WPA-Enterprise Configuration (EAP-TLS):**  
```ini
network={
    ssid="EnterpriseWiFi"
    key_mgmt=WPA-EAP
    eap=TLS
    identity="user@example.com"
    ca_cert="/etc/certs/ca.pem"
    client_cert="/etc/certs/client.pem"
    private_key="/etc/certs/client.key"
    private_key_passwd="mypassword"
}
```

#### **wpa_supplicant ကို Command Line မှ အသုံးပြုရန်**  
```sh
wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf
```
- `-B` → Background mode  
- `-i wlan0` → Wi-Fi Interface  
- `-c /etc/wpa_supplicant.conf` → Configuration file  

Wi-Fi ကို **dhclient** ဖြင့် IP ချမှတ်ရန် -  
```sh
dhclient wlan0
```

#### **GUI Mode (wpa_gui) အသုံးပြုနိုင်လား?**  
`wpa_gui` သည် **Graphical Interface** ဖြစ်ပြီး **Wi-Fi Network များကို GUI မှ ထိန်းချုပ်နိုင်သည်**။  
```sh
wpa_gui
```

#### **wpa_supplicant ကို ဘယ်နေရာတွေမှာ အသုံးချနိုင်မလဲ?**  
- **Linux Laptop/Desktop Wi-Fi ချိတ်ဆက်မှု**  
- **Embedded Linux Devices (e.g. Raspberry Pi, Banana Pi, etc.)**  
- **Industrial & Robotics Wi-Fi Communication (ROM Dynamics AMRs, AI Products, etc.)**  
- **WPA-Enterprise Networks (EAP, RADIUS, Smartcards, TPM Authentication)**  

#### **ဘယ်လို Install လုပ်နိုင်မလဲ?**  
Linux မှာ -  
```sh
sudo apt install wpasupplicant  # Debian/Ubuntu
sudo pacman -S wpa_supplicant   # Arch Linux
sudo dnf install wpa_supplicant # Fedora
```

Windows မှာ -  
[Official wpa_supplicant Windows binaries](http://w1.fi/wpa_supplicant/)

---

**Summary**  
- `wpa_supplicant` သည် Linux/BSD/Windows အတွက် **Wi-Fi Security Supplicant** တစ်ခုဖြစ်သည်  
- WPA/WPA2-PSK, WPA2-Enterprise, 802.1X Authentication (EAP, RADIUS) ကို ထောက်ပံ့နိုင်သည်  
- Command Line (CLI) သို့မဟုတ် GUI (wpa_gui) မှ ထိန်းချုပ်နိုင်သည်  
- Embedded Linux, Robotics, AI Products, Industrial Wi-Fi Applications များတွင် အသုံးပြုနိုင်သည်  

🔥 **ROM Dynamics ရဲ့ AMR & AI Products တွေအတွက် Wi-Fi Security အရမ်းအရေးကြီးတဲ့အတွက် WPA2-Enterprise ကို မဖြစ်မနေ configure လုပ်သင့်ပါတယ်။**
