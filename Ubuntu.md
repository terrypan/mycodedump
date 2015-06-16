# Ubuntu (Misc Stuff) #
SSH Server for remote logins
```
sudo apt-get install openssh-server
```

## Installing Fonts ##
There are various locations in GNU/Linux in which fonts can be kept. These locations are defined in /etc/fonts/fonts.conf; standard ones include /usr/share/fonts, /usr/local/share/fonts, and /home/`<username>`/.fonts (where `<username>` is your user name).

Once the fonts are copied to one of these locations rebuild the font cache:
```
sudo fc-cache -f -v
```

# Ubuntu 12.10 #
superfluous unity lenses like online shopping and amazon stuff. Unfortunately this will remove all unity webapp lenses.
```
sudo apt-remove unity-lens-shopping unity-webapps-common
```


# Ubuntu 11.10 (Oneiric) #

Starting with 11.10 Evolution is not the default mail client anymore. It can safely be removed. As I missed a decent CPU frequency applet, this is how I got it back:
```
sudo add-apt-repository ppa:artfwo/ppa
sudo apt-get update
sudo apt-get install indicator-cpufreq
```

Another, nice one is the Multiload Indicator:
```
sudo apt-get install indicator-multiload
```

## Unity Configurations ##
Unity is a Compiz Plugin. You can configure appearance through the compiz configuration manager:
```
sudo apt-get install compizconfig-settings-manager
```

### Custom Launcher Icons ###
As SSHMenu does not provide an indicator applet I tried HotSSH and Remmina for my SSH connections. But both do not seem to support options for the ssh connection which is just not acceptable.

I ended up creating my own custom launcher icon by copying one of the ".desktop" files in `~/.local/share/applications`

I then modified the settings and drag & dropped it into the launcher.
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=gnome-terminal --profile=remote --command 'ssh my.host.net -p 2222'
Name=my.host.net
Comment=ssh to my.host.net
Icon=gnome-netstatus-idle
StartupNotify=true
```

## SSH Manager ##
SSHMenu does
Switched from SSHMEnu to Remmina due to the switch from gnome to unity. Favoured Remmina over HotSSH as the latter didn't store options for connection.

# Ubuntu 11.04 (Natty) #

## Unity ##
With 11.04 Ubuntu introduces Unity as the new default shell for desktop installations (until now, Unity was only set as default shell on the netbook distribution).

### Indicator Applet ###
The indicator applet is picky about what applications are allowed to add icons. To see the whitelist use:
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```

And to disable the whitelist (i.e. allow all):
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

## Weather Applet ##
```
apt-get install indicator-weather
```

## indicator-sysmonitor ##
```
sudo add-apt-repository ppa:alexeftimie/ppa
sudo apt-get update
sudo apt-get install indicator-sysmonitor
```

The applet does not start automatically, so you eihter start it manually by using the dash and type "System Monitor Indicator" or you add it to the "Startup Applications". The applet can be started with:
```
indicator-sysmonitor
```

# Ubuntu 10.10 (Maverick) #
These are my notes on a fresh Maverick installation. Some of the changes where already introduced with 10.04.

## Nautilus ##
Nautilus has breadcrumbs navigation. To copy and or edit the path within nautilus you need to press Ctrl+L to change into address edit mode.

## Window Controls (introduced with 10.04) ##
In Ubuntu 10.04 the window controls (minimize, maximize, close) have been moved from the top right to the top left. This setting is configurable and can be undone in five steps:

  1. Open a terminal and start `gconf-editor` or go to _Applications > System Tools > Configuration Editor_
  1. Navigate to  _apps > metacity > general_
  1. right click on _button\_layout and choose_Edit Key..._1. change the value to `:minimize,maximize,close`
  1. save your changes with_OK_. Done._

## Filesystem (ext4) Tuning ##

Standard Ubuntu 10.10 installations mount ext4 (and ext3, I guess) with atime. This results in disc writes with every read because the last access is written to disc as well.  This behavior can be deactivated in the fstab by adding `noatime` as parameter to the mount options:

  1. edit fstab: `sudo ne /etc/fstab`
  1. add the `noatime` option (i.e. `UUID=4a19b63e-8644-4eac-ac5e-1af95a727dc7 /               ext4  errors=remount-ro,noatime  0  1`)


## No Drives on Desktop ##
If you would like to get rid of mounted devices on the desktop, this is the solution for you:
  1. Open a terminal and start `gconf-editor` or go to _Applications > System Tools > Configuration Editor_
  1. go to _apps > nautilus > desktop_
  1. uncheck _volumes\_visible_

## Keyboard Adjustments ##
Some fine-tuning on the keyboard configration:
  1. go to _System > Preferences > Keyboard_
  1. change to the tab _Layouts_ and choose _Options_.

Here is a list of useful configurations:
  * Adding EuroSign to certain keys: `E`
  * Key sequence to kill the X server: `Ctrl+Alt+Backspace`
  * Miscellaneous compatibility options: `Default numeric keypad keys` (activates NumLock at startup)

## Empathy Startup on Logon ##
Empathy doesn't automatically start when loggin on to gnome desktop (seems to be a known bug and my be fixed in next releases)
To start Empathy on logon, proceed as follows:
  1. go to `System -> Preferences -> Startup Applications`
  1. click `Add`
  1. Add a new startup entry and add the command:
```
 empathy -h
```

## Full Multimedia Support ##
[Ubuntuguide.org](http://ubuntuguide.org/wiki/Ubuntu:Maverick) provides all information regarding multimedia support.