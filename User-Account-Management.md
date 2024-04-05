## Change user

```bash
su <user>
```
## Ownership and Permission

## User Account management
```bash
useradd
usermod
userdel
```

```bash
sudo useradd -m alex
tail -5 /etc/passwd # view the accounts
```

## Group Management
```bash
groupadd
groupmod
groupdel
```

```bash
sudo groupadd devops_rwx
tail -5 /etc/group
```

Add a user to a group
```bash
sudo usermod -aG devops_rwx larry
cat /etc/group | grep devops_rwx
```

## Creating a Shared Drive
Go to linux `/home` directory. Then `sudo mkdir sharedrive`.

Edit permissions by first changing group, then changing permissions.
```bash
sudo chgrp devops_rwx sharedrive/
sudo chmod 770 sharedrive
```

Then set the inherited group assignment bit. This option forces every file or directory made in the sharedrive directory to have the same initial group (share_access) as the sharedrive directory itself. This will allow anyone in the devops_rwx group to read, write, and execute any directory or file in the sharedrive folder.
```bash
sudo chmod g+s sharedrive
```
