#OpenWrt MT7620
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
opkg install --force-overwrite ip ipset openssl-util
opkg install --force-overwrite iptables-mod-nat-extra luci-i18n-qos-zh-cn
opkg install --force-overwrite luci-i18n-samba-zh-cn luci-i18n-upnp-zh-cn luci-i18n-minidlna-zh-cn
   
```
-------------------------------------------------------------------------------
adbyby
```
cd /tmp && wget --no-check-certificate -O adbyby.tar.gz "https://raw.githubusercontent.com/0oVicero0/OpenWrt_MT7620/master/adbyby.tar.gz" && tar -xvf adbyby.tar.gz && cd adbyby && sh Install.sh
```
