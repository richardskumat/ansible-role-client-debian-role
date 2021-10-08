ansible-role-client-debian-role
=========

Sets up a linux xfce4 desktop environment with my preferences.

I thought about setting up a separate role for each major task group this
role currently has with the release of Debian 11, but since it's a
personal role I'm not really interested in doing so.

Requirements
------------

Tested on:

ansible > 2.9

Role Variables
--------------

```
form_factor: desktop
```

Separate tasks based on device form factor. In my case, it's only two devices, so
valid values are 'desktop' or 'laptop'.


```
blacklist_modules: [
  "# intel me mods",
  "#blacklist mei",
  "#blacklist mei_me",
  "# iAMT Watchdog Device",
  "#blacklist mei_wdt",
  "#blacklist uas",
]
```

These modules are to be blacklisted, based on personal preference. Used in a templating task.

```
# libreoffice
lo_hide_eula: '1'
lo_logo: '0'
```

These values are required to disable libreoffice's logo on start, reducing start up time.
Used in a templating task.

```
# seagate externals
external_drive_quirks: [
  '#options usb-storage quirks=0bc2:3343:u',
  ]
```

# https://www.kernel.org/doc/html/latest/admin-guide/kernel-parameters.html

This value is used in a templating task. This options tells the kernel to not use the uas
module for this drive.

# systemd settings
systemd_system_conf: [
  'DefaultTimeoutStartSec=10s',
  'DefaultTimeoutStopSec=10s',
]

Set some values for /etc/systemd/system.conf in a templating task.

Dependencies
------------

Possibly my other roles, eg

richardskumat.ansible_role_common

richardskumat.ansible_role_grub_cmdline

richardskumat.ansible_role_user

License
-------

GPLv3

Author Information
------------------

Richard Skumat

https://github.com/richardskumat/
