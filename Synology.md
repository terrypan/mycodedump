

# Introduction #

The documentation is tested on a Synology 411+. If not stated otherwise the latest stable Disk Manager software is used.

The hostname of the Synology device used in the examples is _tank_. You should replace it with the hostname or the ip address of your device of course. ;)

# Remote Shutdown #
If ssh is enabled use root to log in and the admin password to authenticate:
```
ssh root@tank
poweroff
```

# Auto mount Synology share on Linux with CIFS enabled #
Add the mount to the /etc/fstab file:
```
#CIFS Share
//syno/home /media/Local-Folder cifs credentials=/home/username/.mycredentials,iocharset=utf8,sec=ntlm 0 0
```
Create the corresponding .mycredentioals in your home dir with the content below:
```
username=cifs-username
password=xxx
```