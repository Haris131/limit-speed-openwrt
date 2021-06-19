# limit speed openwrt
1. install nya via Terminal dengan perintah:
```
opkg update && opkg install iptables-mod-hashlimit iptables-mod-iprange
```

# Pasang Rule
Bandwidth limiter dapat anda pasang dengan menggunakan rules berikut ini, bagi yang menggunakan LuCI dapat menambahkan rules nya di bagian Network -> Firewall -> Custom Rules
```
iptables -I FORWARD -m iprange --dst-range 192.168.1.11-192.168.1.254 -m hashlimit --hashlimit-above 16kb/s --hashlimit-mode dstip --hashlimit-name lambat -j DROP
```
Rules tersebut akan membuat perangkat di rentang ip tersebut hanya memiliki kecepatan download maksimal 16KB/s (kadang lebih dikit). Kecepatan uploadnya tidak saya limit karena kasian.

iptables merupakan utility yang umum ada pada sistem operasi linux. Rule diatas dapat juga diaplikasikan pada sistem operasi linux lainnya seperti Ubuntu dan Debian.
