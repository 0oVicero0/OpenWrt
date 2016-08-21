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
USB
```
opkg install kmod-usb-core kmod-usb-ohci kmod-usb-uhci kmod-usb2 kmod-usb-storage 
opkg install kmod-usb-storage-extras block-mount kmod-ledtrig-usbdev mount-utils fdisk usbutils
opkg install kmod-fs-exfat kmod-fs-vfat kmod-fs-ext4 kmod-fs-ntfs ntfs-3g
opkg install kmod-nls-cp437 kmod-nls-iso8859-1 kmod-nls-utf8
     
```
vi /etc/hotplug.d/block/10-mount
```
#!/bin/sh

# Copyright (C) 2009 OpenWrt.org  (C) 2010 OpenWrt.org.cn

blkdev=`dirname $DEVPATH`
if [ `basename $blkdev` != "block" ]; then

    device=`basename $DEVPATH`
    case "$ACTION" in
        add)
                mkdir -p /mnt/$device
                # vfat & ntfs-3g check
                if  [ `which fdisk` ]; then
                        isntfs=`fdisk -l | grep $device | grep NTFS`
                        isvfat=`fdisk -l | grep $device | grep FAT`
                        isfuse=`lsmod | grep fuse`
                        isntfs3g=`which ntfs-3g`
                else
                        isntfs=""
                        isvfat=""
                fi

                # mount with ntfs-3g if possible, else with default mount
                if [ "$isntfs" -a "$isfuse" -a "$isntfs3g" ]; then
                        ntfs-3g -o nls=utf8 /dev/$device /mnt/$device
                elif [ "$isvfat" ]; then
                        mount -t vfat -o iocharset=utf8,rw,sync,umask=0000,dmask=0000,fmask=0000 /dev/$device /mnt/$device
                else
                        mount /dev/$device /mnt/$device
                fi
  if [ -f /dev/${device}/swapfile ]; then
   mkswap /dev/${device}/swapfile
   swapon /dev/${device}/swapfile
  fi
                ;;
        remove)
  if [ -f /dev/${device}/swapfile ]; then
   swapoff /dev/${device}/swapfile
  fi
                umount /dev/$device
                ;;
    esac

fi
   
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
