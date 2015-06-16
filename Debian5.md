# Installed Packages #

Installation protocol for Debian 5 Setup:
`apt-get install` the following packages:
Misc:
```
ne exim4 cron-apt ntp ntpdate NcFTP subversion curl
```


LAMP:
```
apache2 apache2-suexec php5 mysql-server mysql-client php5-cli php5-curl php5-mhash php5-tidy mcrypt phpmyadmin
```

# Configuration #
Installed German locale with (should maybe set de\_DE.UTF-8 as default):
```
dpkg-reconfigure locale
```
Add user with `adduser <username>`
Exim Configuration:
```
dpkg-reconfigure exim4-config
# Timezone konfigurieren
dpkg-reconfigure tzdata
```


--- lamp config ----
prevent banner disclosure on apache2

In the configuration file, add:
ServerTokens ProductOnly

And the header is reduced to:
Apache


- ssh setup
http://www.howtoforge.com/set-up-ssh-with-public-key-authentication-debian-etch
- set port to 2222

## offene punkte ##
  * root pw für mysql user ändern?