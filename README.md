# [MATE Desktop Environment](http://www.mate-desktop.org/) ports collection for [CRUX](https://crux.nu/) Linux #

## The current release is MATE 1.18 for CRUX 3.3 (as of 09 Apr 2017) ##

## Quickstart ##

Download mate.httpup:

```
curl -o /etc/ports/mate.httpup https://raw.githubusercontent.com/mhoush/crux-mate/master/mate.httpup
```

Enable the 'contrib' ports collection as [described in the CRUX handbook](https://crux.nu/Main/Handbook3-2#ntoc42)

Add 'prtdir /usr/ports/mate' to **/etc/prt-get.conf**, preferably before 'contrib', 'core', 'opt', and 'xorg'.

Update ports collections:

```
ports -u
```

Install MATE ports:

```
prt-get depinst mate --install-scripts
```

After the installation completes, add dbus to the 'SERVICES' array in /etc/rc.conf:

```
SERVICES=(net crond dbus)
```

If using startx configure your .xinitrc like so:

```
exec /usr/bin/start-mate
```

If using a login manager or other method, configure as appropriate.
