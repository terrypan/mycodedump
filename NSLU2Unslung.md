## How to Unsling an NSLU2 ##

More or less step by step instruction on my Unslung NSLU2, providing Samba Fileshare and media server services.

1. Latest Unslung Release (6.10-beta)
http://www.slug-firmware.net/u-dls.php

2. prepaired 512MB USB memory stick as main drive
http://www.nslu2-linux.org/wiki/HowTo/UseAMemoryStickAsMainDrive
(formatted on an Ubuntu client, modified fdisk)

3. Unsling to USB stick on interface "Disk2"
http://www.nslu2-linux.org/wiki/Unslung/WhichUSBPortforUnslung6

4. changed URL to optware packages:
vi /etc/ipkg/native-feed.conf
change URL to:
http://ipkg.nslu2-linux.org/feeds/optware/nslu2/native/stable/

5. Install ushare
http://www.nslu2-linux.org/wiki/Applications/UShare

6. Modify config file and startup script
/opt/etc/ushare.conf:
  * USHARE\_PORT=49200
  * USHARE\_DIR=/share/disk1/music,/share/disk1/pictures,/share/disk1/movies
  * USHARE\_ENABLE\_WEB=no
  * USHARE\_ENABLE\_TELNET=no
  * USHARE\_ENABLE\_XBOX=no
  * USHARE\_ENABLE\_DLNA=no

Modified /opt/etc/init.d/S99ushare (ushare deamon does not write any .pid files and therefore the script didn't stop the service:
```
stop() {
        echo -n "Stopping $DESC... "
        killall -9 ushare
        echo "done"
}
```

7. Formatted and attached 250gb drive to "Disk1" interface. Needs special formatting because Unslung does not support 256 byte inode sizes. Therefore format the storage with 128 byte sized inodes:
> mkfs.ext2 -j -I 128 -m 0 /dev/sdb1
-j makes it journaling (Ext3)
-I 128 forces the inode size to 128
-m 1 reduces the amount of space on the partition allocated to root to 0%.

8. added a mount to /shares/disk1/
```
$ cat /unslung/rc.samba 
  #!/bin/sh
  /bin/mount /dev/sdb1 /share/disk1
  return 1
$ 
```

9. Adjusted samba(/etc/samba/user\_smb.conf):
for each share:
[movies](movies.md)
valid users=@"administrators",@"everyone"
comment=Movies
path=/share/disk1/movies
browsable=yes
write list=@"administrators",@"everyone"

10. chmod 0777 on /shares/disk1 and all subfolders

Although the drive is not accessible through the web interface, it works flowless with my WD box. I was unlucky with my Webradio so far, but I may look into that on another occasion.