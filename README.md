#OpenWrt MT7620
-------------------------------------------------------------------------------
Reset
-------------------------------------------------------------------------------
```
firstboot -y && reboot
```
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
Install
```
opkg update
opkg install --force-overwrite luci-i18n-base-zh-cn
opkg install --force-overwrite ip ipset openssl-util libgmp libnettle
opkg install --force-overwrite iptables-mod-nat-extra luci-i18n-qos-zh-cn
opkg install --force-overwrite luci-i18n-samba-zh-cn luci-i18n-upnp-zh-cn luci-i18n-minidlna-zh-cn
   
```
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
MWAN3
```
opkg install kmod-macvlan luci-app-mwan3 dnsmasq-full

ip link add link eth0.2 name vth0 type macvlan
ifconfig vth0 up

Network->Load Balancing->Configuration->Interfaces (new, Input your Interfaces )
Network->Load Balancing->Configuration->Members (new, Metric = 1,Weight = 1 )
Network->Load Balancing->Configuration->Policy (new, Last resort = default )
```
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
adbyby
```
cd /tmp && wget --no-check-certificate -O adbyby.tar.gz "https://raw.githubusercontent.com/0oVicero0/OpenWrt_MT7620/master/adbyby.tar.gz" && tar -xvf adbyby.tar.gz && cd adbyby && sh Install.sh
   
```
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
