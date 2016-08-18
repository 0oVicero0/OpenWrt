#OpenWrt MT7620
-------------------------------------------------------------------------------
Install
```
opkg update
opkg install ipset
opkg install openssl-util
opkg install luci-i18n-qos-zh-cn
opkg install luci-i18n-upnp-zh-cn
opkg install luci-i18n-minidlna-zh-cn
```
-------------------------------------------------------------------------------
adbyby
```
wget --no-check-certificate -O adbyby.tar.gz "https://raw.githubusercontent.com/0oVicero0/OpenWrt_MT7620/master/adbyby.tar.gz" && tar -xvf adbyby.tar.gz && cd adbyby && sh Install.sh
```
