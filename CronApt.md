## Introduction ##
Cron-Apt is a program, that can operate scheduled tasks on apt-get including e-mailing the output of apt-get calls.

Our goal is to configure cron-apt to send out e-mails and notify us, if new updates are available.

## Installation ##
```
apt-get install cron-apt
```

## Configuration ##
Add the following configuration to the cron-apt actions in `/etc/cron-apt/action.d/`:
  * `0-update` - This updates the local cache of the repository to the latest releases and should be run first (therefore starting with a `0`):
```
update -o quiet=2
```
  * `9-notify` - This _simulates_ a dist-upgrade and only generates output if there is something to upgrade. The benefit of using `dist-upgrade` instead of `upgrade` is, that this checks for new distributions as well as long as you have generic repository sources (i.e. "stable" instead of "edgy" etc.):
```
# Use it with MAILON=output to tell you when upgrades are available.
-q -q --no-act dist-upgrade
```

On each call of cron-apt, this will first of all update the local cache from the repository with `apt-get update -0 quiet=2` and then simulate a dist-upgrade. You don't actually want to run automatic updates without watching at them on a production server, don't you? ;-)

With some distributions (like Debian) you get a `3-download` action already set up. This action is too verbose by default, but you can modify it to a bit to keep the functionality (download available packages) and still only get emailed if updates are actually available:

```
autoclean -y -qq
dist-upgrade -d -qq
```

Additionally you should get a cron.d configuration ready to use (`/etc/cron.d/cron-apt`):
```
#
# Regular cron jobs for the cron-apt package
#
# Every night at 4 o'clock.
0 4	* * *	root	test -x /usr/sbin/cron-apt && /usr/sbin/cron-apt
# Every hour.
# 0 *	* * *	root	test -x /usr/sbin/cron-apt && /usr/sbin/cron-apt /etc/cron-apt/config2
# Every five minutes.
# */5 *	* * *	root	test -x /usr/sbin/cron-apt && /usr/sbin/cron-apt /etc/cron-apt/config2
```

Now that we've already set up everything to check for new updates, we need to configure our e-mail address to get notified of available updates (edit `/etc/cron-apt/config`):
```
# The email address to send mail to.
 MAILTO="your-email@mail.com"

# Value: error   (send mail on error runs)
#        upgrade (when packages is upgraded)
#        changes (mail when change in output from an action)
#        output  (send mail when output is generated)
#        always  (always send mail)
#                (else never send mail)
 MAILON="output"
```

Actually there's a bunch of other things you may want to configure. The configuration file is quite self-explanatory.