backup-mikrotik
===============

A simple tool to back up Mikrotik devices. Requires bash, ssh, and sftp.

Installation
===============

Just copy any where in your path, and make executable. You may want to
change the USER="root" line to USER="admin", or whatever your preferred
user is on Mikrotik.

Recommendations
===============

Create a user on your Mikrotik devices with a trusted SSH DSA key. This
allows backup-mikrotik to avoid prompting you multiple times for passwords.

Mikrotik accepts only DSA SSH keys. Once a Mikrotik user accepts an SSH
key, it no longer allows password authentication, even in Winbox. So do
not do this with your "admin" user; create another user for this purpose
instead. I use "root" for this.

# On your workstation:
scp ~/id_dsa.pub admin@10.0.0.1:/

# On your Mikrotik device:
/user
user add name=root group=full password=xxxxxxxx
user ssh-keys import user=root public-key-file=id_dsa.pub
