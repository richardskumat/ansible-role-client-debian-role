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
# libreoffice
lo_hide_eula: '1'
lo_logo: '0'
```

These values are required to disable libreoffice's logo on start, reducing start up time.
Used in a templating task.


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
