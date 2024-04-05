**Commands:**

- **ps:** views information related to the processes on a system, reads from /proc file-system
     - **ps -f:** shows the process ID and the parent process ID
     - **kill:** terminates process ID (if ignored, use kill -9 followed by process ID)
     - **PID:** the unique process ID
     - **TTY:** terminal type user is logged into
     - **TIME:** amount of CPU in minutes and seconds that process has been running
     - **CMD:** name of the command that launched the process
- **chrony:**
     - **systemctl status chronyd:** check chronyd status (chrony.conf file specifies NTP server)
     - **systemctl start chronyd:** start the service
     - **/etc/chrony.conf** or **/etc/chrony/chrony.conf**: configuration files that store NTP info
- **/etc/passwd:** user account and pwd info
- **/etc/shadow:** holds encrypted pwd of corresponding accounts
- **/etc/group:** contains group information for each account
- **/etc/gshadow:** contains secure group account info

- **Managing user accounts/group assignments:**

     - **sudo useradd -m 'name':** creates a new user using sudo permissions and creates a home directory
     - **sudo passwd 'name':** assigns a password to a user using sudo permission
     - **tail -5 /etc/passwd:** verify users were created by viewing this file
     - **sudo usermod -aG 'groupname' 'user name':** adds a user to a group
     - **sudo usermod -c < "Comment" > < username >:** adds a comment to a user
     - **cat /etc/group | grep 'groupname':** views accounts that are within the group
     - **sudo chgrp 'groupname' 'directoryname':** changes group of directoryname to groupname
     - **sudo chmod g+s 'directoryname':** every file or directory made in 'directoryname' will have intial group as that directory
- **Groups:**
     - **useradd:** adds accounts
     - **usermod:** modifies account attributes
     - **userdel:** deletes accounts
     - **groupadd:** adds groups
     - **groupmod:** modifies group attributes
     - **groupdel:** removes groups