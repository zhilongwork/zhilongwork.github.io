##

```bash
sudo -S apt update -y
sudo -S apt install samba smbclient -y
sudo -S tee -a /etc/samba/smb.conf >/dev/null << eof

[share]
comment = Shared Folder require password
path = /home/$USER
writable = yes
available = yes
browseable = yes
eof

sudo smbpasswd -a $USER
sudo /etc/init.d/smbd restart
```
