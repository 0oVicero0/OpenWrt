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
Multiwan
```
opkg install http://downloads.openwrt.org/barrier_breaker/14.07/ramips/mt7620a/packages/oldpackages/multiwan_1.0.22-2_ramips_24kec.ipk
opkg install luci-i18n-multiwan-zh-cn
```
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
adbyby
```
cd /tmp && wget --no-check-certificate -O adbyby.tar.gz "https://raw.githubusercontent.com/0oVicero0/OpenWrt_MT7620/master/adbyby.tar.gz" && tar -xvf adbyby.tar.gz && cd adbyby && sh Install.sh
```
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
