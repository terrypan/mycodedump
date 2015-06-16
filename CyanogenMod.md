# Introduction #

tbd


# CyanogenMod 7.1 nightly on HTC Hero (GSM) #

Rooted Phone: http://www.freeyourandroid.com/guide/rooting_htc_hero_androot

Nightly Builds: http://download.cyanogenmod.com/?type=nightly&device=hero

Changelogs: http://cm-nightlies.appspot.com/?device=hero

Flash Image: http://wiki.cyanogenmod.com/wiki/Flash_image

Update Guide: http://wiki.cyanogenmod.com/index.php?title=HTC_Hero_(GSM):_Full_Update_Guide

FAQ: http://wiki.cyanogenmod.com/wiki/HTC_Hero_(GSM):_FAQ

Boot into the Amon\_Ra's Recovery, by pressing the Home button while powering on.


# CyanogenMod on HTC Desire S (GSM) aka Saga #

  1. Backup all your data (SMS Backup etc.)
  1. download latest CM10 alpha release here: http://forum.xda-developers.com/showthread.php?t=1776256 (don't forget to download the google apps as well) and get a recovery tool (I used 4EXT\_Recovery\_v2.2.7\_RC5)
  1. Unlock Bootloader via HTCDev.com (chose all other devices)
  1. now that you have a working command line and already unlocked the bootloader you can flash the custom recovery:
  1. push volume down button and power button to boot into bootloader
    1. chose "fastboot"
    1. on the command line execute "fastboot flash recovery recovery.img"
  1. now, select "recovery" in the bootloader menu to boot into the newly flashed recovery
  1. you should now see 4EXT Recovery start screen. go to "wipe data" and delete both caches and format all mount points except sdcard (system, boot, data) and make sure they are all formatted as ext4 filesystem. My DS didn't boot until i did exactly this.
  1. install your rom (zip) and the latest google apps
  1. reboot back into the bootloader (fastboot) and flash the boot.img in addition (this again was necessary to successfully boot CM10 >fastboot flash boot boot.img
  1. now reboot and enjoy :)

### Adding better aGPS support ###
Forum: http://forum.xda-developers.com/showthread.php?t=1442032
Get the ADB Push Installer with various patches from here:
http://derekgordon.com/gps-files/agps.adb.all.builds.v3.1.and.v1.3.zip

  1. (enable usb debugging)
  1. boot into recovery
  1. mount /system
  1. run the .bat or .sh script (depending on your OS)