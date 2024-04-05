### Package Management
Installing, Updating, Removing, Software specific repositories.
- RPM (Red had package manager)
- YUM (Yellow Dog Updater, Modified) Yum was the primary package in Red Had and still available. YUM performs dependency resolution. YUM can manage packages in system or from .rpm.packages.
- DNF (Dandified YUM) default manager in RHEL > 8 sports better dependency resolution (which version to install), optimized memory intensive operations, run python 2 and 3, complete documentation for python APIs. You can even delete Kernel packages.

### System Logging
Critical to events, need to see cause of issuels, Linux has flexible system, captires varios processes to a log dile to manipulate logs to retrieve info you require.

#### Syslog
- Linux provided facility. Programs send to syslog, the host is configurable and uses central system logging process at `/etc/syslogd` or `/etc/syslog`.

- Can do actions like: write to log file, echo message to console, write to logged in user, send the message along to another syslog server, not to log. 
- Syslog has indicators of importance arranged in 8 (0-7) levels of priority with 7 (debug) being the lowers and 0 being the highest (emergency)
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/baf51092-72c9-4569-a914-80c745d359e6)

## System Time
### NTP Network Time Protocol
Keeps clocks synced with each other in a network. NTP servers have access to atomic and GPU clocks. It uses UTC to synchronize CPU. Avoids fraction of vulnerabilities.

NTP uses hierarchical system of time and provides with stratum servers. First at the topmost level there is highly accurate time resources ex atomic or GPS clocks. These clocks are called **statum 0** sercers and they are linked below to NTP servers that are **Stratum 1,2,3...**

## Process Management
When you execute a program on Linux you get a environment for that program. It has everything needed for program to run. The program and its environment is called process. The OS tracks process with 5 digit ID or the PID. Each is unique. When starting you can start two ways:
1. Foreground Processes
2. Background Processes - simplest way to start background is to add & at the end of the command

- `ps` command (process status) shows inofrmation. It reads process infomation from /proc system file. It has virtual files.

`ps [options]` is the syntax, the output has the following
- PID unique ID
- TTY terminal type user is logged into
- TIME amount of CPU in minutes that has been running
- CMD name of command that launched process

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/4deef6b0-5325-4b95-8818-980c5ce4f7c1)

Each unix has two IDs, you can see with `proc -f`
- PID
- PPID - parent process ID of parent process, most commands have the shell as the parent

Ending process can be done with `ctrl C`, if its in the background get the Job ID and use `kill [job ID]` command.

**SLIDE 26 and 27**

### Configure Client-side NTP Using chronyd
Chrony is a NTP implementation. It can sync sys clock with NTP servers, ref clocks, and manual iput. Allow other systems to updates as a server peer. Syncs internal clock with higher stratum NTP server, reference clock, or the computers real time clock. On a LAN the precision is usually within miliseconds
- Chronyc is a command line interface for monitoring and tweaking chronyd output
- chronyd is a backgorund daemon that starts and activates chrony NTP service and tracks time and status of time server
-  obtains one of the major NTP server sources
- if server time is off it will sync
- `crony.conf` file specifies time NTP server that chronyd tracks
- check chronyd status using `systemctl status chronyd`
**SLIDE 32**

## Manage User Groups and Accounts
- Root Account - super user without restriction, assumed system admin
- System Account - operations of system specific components (mail and sshd), they are needed to functions on system

### Four Main User Admin Files
1. `/etc/passwd` keeps user account and password information, this file holds the majority of information on Unix system, username, user ID, and group ID, user ID info, user home directory, and login shell, owned by root and has rw-r--r-- permissions, only root can write to it.
2. `/etc/shadow` - Holds the encrypted password of the account, not all systems support this file
3. `/etc/group` contains the group information for each account
4. `/etc/gshadow` this file has secure group account information

### Managing Permissions
Each file has bits for read, write, execute at three levels, owner, groups, and everyone.
- written as r w or x
- `-` means a regular file `d` means a directory
- you may use octal (777) or binary translations to set the permissions with `chmod`

### Managing Users
To create and manage accounts we use the following commands:

- `usermod` modifies account attributes
- `userdel` deletes accounts
- `groupadd` adds group
- `groupmod` modifies group attributes
- `groupdel` removes group 

Creating accounts with `useradd` command
- `useradd` adds accounts
  - `useradd -d homedir -g groupname -m -s shell -u userid accountname`
  - `d homedir`	specifies home directory for the account
  - `g groupname` specifies a group account 
  - `m` creates the home directory if it doesn’t exist
  - `s shell` specifies the default shell
  - `u userid` specifies a user id
  - accountname is the name of the account to be created

Creating groups using `groupadd` syntax
`groupadd [-g gid [-o]] [-r] [-f] groupname`
Option descriptions:
- `g` the numerical value of the group ID (GID)
- `o` permits to add group with non-unique GID
- `r` instructs groupadd to add system account
- `f` causes to just exit with success status, if the specified group already exists. 
Groupname is the name of the group to be created

```bash
sudo usermod-aG <group> <user to add>
```




