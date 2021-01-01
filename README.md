# [MATE Desktop Environment](http://www.mate-desktop.org/) ports collection for [CRUX](https://crux.nu/) Linux #

## The current release is MATE 1.24 for CRUX 3.6 (as of 1 Jan 2021). ##

## Quickstart ##

Download mate.httpup:

```
curl -o /etc/ports/mate.httpup https://raw.githubusercontent.com/mhoush/crux-mate/main/mate.httpup
```

Enable the 'contrib' ports collection as [described in the CRUX handbook](https://crux.nu/Main/Handbook3-6#ntoc46)

Add 'prtdir /usr/ports/mate' to **/etc/prt-get.conf**, **before** 'contrib', 'core', 'opt', and 'xorg'.

Update ports collections:

```
ports -u
```

Add the collection's public key to the ports config:

```
cp /usr/ports/mate/mate.pub /etc/ports/
```

Install MATE ports:

```
prt-get depinst mate --install-scripts --margs="-in"
```

**NOTE:** There are a few ports outside of the MATE ports tree that will likely have footprint mismatches during the MATE build. These mismatches are usually due to extra libraries or software installed that the ports detect. The **--margs="-in"** option to prt-get above will cover cases of NEW files in .footprints.

After the installation completes, add dbus to the 'SERVICES' array in /etc/rc.conf:

```
SERVICES=(net crond dbus)
```

Ensure the dbus service is running or reboot.

If using startx configure your .xinitrc like so:

```
exec /usr/bin/start-mate
```

If using a login manager or other method, configure as appropriate.
