

## Shell Tools ##
### Tar Backups ###
Backup:
```
tar -czf ./file.tar.gz ./dir/
tar -czf /path/to/file/file.tar.gz /path/to/dir/
```
Restore:
```
tar -xfv ./backup.tar.gz --overwrite
```

### Find ###
To find a file such as filename.txt anywhere on the system:
```
find / -name filename.txt -print
```

Do a recursive search and modify permissions on directories
```
find . -type d -name public_html -exec chmod 0755 {} \;
```

Find within files:
```
sudo find / -iname <string>
```

Find files and remove them:
```
find ./ -iname 'Picasa.ini' -exec rm -f {} \;
```

### ImageMagick ###
Reduce quality on all files in a directory:
```
for i in *.jpg; do convert $i -quality 80% web-$i.jpg; done
```

## Web and Mail Management ##
### MySQL ###
Import Dump into Database:
```
mysql --user=user --password=xxx <db-name> < ./dump.sql
```

Backup DB:
```
mysqldump -u [username] -p --opt [databasename] > [backupfilename.sql]
mysqldump --all-databases -u admin -p > full-backup.sql
```
### Apache2 ###
  * Use 'apache2ctl configtest' to test apache2 config before restarting...
  * Use /etc/apache2/sites-enabled/myapache2.conf to save custom settings which should be activated for all sites.

### SSH ###
Protect from server from the dumbest dictionary attacks by changing the ssh port from 22 to 2222.

Check for root logins via ssh:
```
cat /var/log/auth.log | grep ssh.*root | less
```

Check who is logged in right now:
```
w
```

### qMail ###
/dev/null with qmail:
If you are hosting several virtual domains you are usually not interested in double bounces that qmail delivers to the postmaster of the default mail host (actually double bounces are sent to postmaster@doublebouncehost, where doublebouncehost defaults to me and is defined in the file qmail/control/me). Usually me should be just fine. All we need is an address at that host, that removes the bounce mail silently from the qmail queue.

Therefore we create the file doublebounceto in qmails control folder and add devnull to the first line. To receive mails to devnull@me we create the file .qmail-devnull in qmail/alias/ and add a comment on the first line:
```
 # throw messages away undelivered
```
This will effectively remove the doublebounce from the queue.

## Network ##

### nslookup ###
```
reto@morpheus:~$ nslookup
> set type=mx
> theater-ueberland.ch
Server:		62.2.24.162
Address:	62.2.24.162#53

Non-authoritative answer:
theater-ueberland.ch	mail exchanger = 5 server15.cyon.ch.

Authoritative answers can be found from:
server15.cyon.ch	internet address = 194.126.200.25
```
### Network Setup ###
```
edit /etc/network/interfaces
/etc/init.d/networking restart
```

### Adding Nameservers ###
  1. `sudo ne /etc/resolve.conf`
  1. search _nameserver 192.168.0.1_
  1. add more name servers to the list

### NMAP ###
`nmap -sS -O -p 135-139 -oN e:\log.txt  217.162.*.*`

### Arp ###
List all Devices in the local network `arp -e`

## Hardware ##
### Bluetooth ###
Pair Bluetooth devices:
  1. Run `$ passkey-agent --default /usr/bin/bluez-pin`
  1. connect with the device and enter the pass

### HDD ###
S.M.A.R.T Disk Daten auslesen:
sudo smartctl -a -d ata /dev/sdb

hdparm settings:
  * Empfohlenes Accoustic Management Level
> > `sudo hdparm -M 254 /dev/sdb`
  * Standby (240 **5 = 1200 / 60 = 20min)
> > `sudo hdparm -S 240 /dev/sdb`
  * setting drive keep features to 1 (on)
> > `sudo hdparm -K 1 /dev/sdb`**

### GFX Driver ###
Test GLX:
```
glxinfo | grep rendering
```

## Misc ##
change user and group recursive:
```
chown -R user:group ./*
```

Change access writes recursive:
```
chmod -R 0777 ./*
```

Copy recursively:
```
cp -R ./test1/* ./test2/
```

Patch files:
```
patch -cl -d [DIRECTORY] -p1 < [PATCH NAME]
```

Bzip2 Bombs (100 x 1kb = 100mb):
```
dd if=/dev/zero bs=1024 count=100 | bzip2 -cv > test.bz2
```

Find UUID of a disk (i.e. to set mounts in fstab via UUID):
```
ls -l /dev/disk/by-uuid
```

Count amount of files recursively within a directory:
```
for d in *; do echo -n "$d: "; find $d -type f | wc -l; done
```

List available Inodes:
```
df -i
```

## Links ##
  * [Cron Syntax Reference](http://adminschoice.com/crontab-quick-reference)