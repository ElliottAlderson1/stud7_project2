

# Other Commands 


```
| - pipes output of one command to another.
tail -f - follow the bottom of a file.
     -n - display number of lines
```

## Tar Commands


tar creates tar files by converting files into an archive.
```
tar -c - Create an archive
tar -x - extract the archive
tar -f - creates with given name
tar -t - list contents of tar
tar -z - creates tar file using zip
tar -r - update/add to an existing tar
tar -delete - remove file from tar

tar variations:
.tar - tar
.tar.gz - gzip = -z
.tar.bz2 - bzip = -j
.tar.xz - xzip = -J
```

## IP commands

```
ip address add <IP> dev <int> - adds ip address to certain interface.
```

## System Admin Commands
Not a command, but syslog is what is used for logs. Usually stored in /etc/syslog | syslogd

```
ps - check what processes are running.
   - aux - list all
   - f - list more info, including what parent ran the command (PPID)

chrony - NTP implementation.
   chronyd - background
   chronyc - cli tool
   configurations are located in /etc/chrony.conf
```

## System Administration Commands
- ```sudo useradd -m <user>``` - Create a new user with a home directory
- ```sudo passwd <user>``` - Change the password of a user
- ```sudo groupadd <name>``` - Create a new group with the given name
- ```sudo usermod -aG <group> <user>``` - Add the user to the group
   - ```-c <Info> <user>``` - Adds given information to the user
- ```sudo chgrp <group> <directory/file>``` - Change the group of a directory to given group
- ```sudo chmod g+s <directory/file>``` - Forces all files/directories created in this folder to have the same group as the given directory.
- ```su``` - Switch user

### System Administration Verification Commands
- ```cat /etc/passwd``` - Contains users and any extra info provided.
- ```cat /etc/groups``` - Contains group information.

1. ssh-keygen -t -b 2048
2. Enter file to save to
3. Enter passphrase
4. Public is .pub/Private no file extension.

### SSH bug fix
```restorecon -R -v ~/.ssh```

## SSH Key Pair Generation
**Process For Generating Keys**
1. The following commands are all executed from the command line on your workstation:
**ssh-keygen -t rsa -b 2048**
2. Which will display the following:
**Generating public/private rsa key pair. 
Enter file in which to save the key (/root/.ssh/id_rsa):** 
3. Hit Enter to accept the default location. Next the system will show:
**Enter passphrase (empty for no passphrase):**
4. So just hit Enter here. Finally, it will ask for you to re-enter the passphrase:
**Enter same passphrase again:**
5. So hit Enter a final time.

You now should have an RSA type public and private key pair in your .ssh directory:

**cat ~/.ssh/id_rsa**

**cat ~/.ssh/id_rsa.pub**

**. .. id_rsa id_rsa.pub**