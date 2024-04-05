# Lab 03 Introduction to Redirection and Piping
Redirect the standard output and standard error to the same file:
~~~bash
ls video.mpeg blah.foo > myoutput 2>&1
~~~
The `&1` on the the end is a pointer to the standard input. Combining this `&1` with the `2>` command tells the Linux shell to redirect any `standard error` to the `standard input`. Then, any of these `standard errors` that were redirected to the `standard input` are redirected to the `myoutput` file.

# Lab 04 Search, Extract and Archive Data
Do not forget the `.` on the `cp` command sometimes for referencing current directory.
~~~bash
cp /usr/share/dict/words .
~~~
Make sure to use `-E` on grep for treating as regular expressions such `grep -E 'dogs$' words`.
Filter outputs of commands like: 
~~~bash
ls /etc | grep -E 'sys'
~~~
Tar in practice commands
- `cf`: Creates a tar file.
- `tf`: Looks at the contents of a tar file.
- `rf`: Adds a file to a tar file.
- `xf`: Extracts a non-compressed tar file.
- `czf`: Creates a compressed tar file using gzip (.tgz file extension).
- `xzf`: Extracts a compressed tar file.

# Lab 05 Introduction to Networking

127.0.0.1 is always the IPv4 address of the loopback interface.

Turn off or on the loopback network interface using sudo permission:
~~~bash
sudo ip link set lo down
sudo ip link set lo up
~~~
Add the IP address 172.200.200.200/24 to your interface using sudo permission, then restart network manager:
~~~bash
sudo ip address add 172.200.200.200/24 dev <interface name>
sudo systemctl restart NetworkManager
# To delete
sudo ip address del 172.200.200.200/24 dev ens34
~~~
To add the new DNS entry to new interface:
~~~bash
sudo nano /etc/hosts
#add 172.200.200.200   mycomputer
~~~
Lookup a Domain server and add it to /etc/resolv.conf
~~~bash
nslookup google.com
# add name server nameserver 8.8.8.8
~~~

# Lab 06 Package Management

~~~bash
yum repolist #See current repositories in use
ls /etc/yum.repos.d #yum repo config files
yum list #available packages
yum search wireshark #alternative to grep
yum list installed #see installed packages for rpm
yum info httpd #info about a package
~~~

~~~bash
sudo systemctl status httpd #check status of a service (httpd)
sudo systemctl start httpd #starts service
sudo systemctl enable httpd #ensure service starts with VM or Linux
sudo systemctl stop httpd #stops service
sudo yum remove httpd #remove package
~~~

~~~bash
ps aux #view all the processes running
~~~

~~~bash
top #View the current status of system resources 
free #View the current availability of system memory
watch free #Watch the free command periodically update
kill -9 3650 #Kill the watch process using the format
~~~

# Lab 07 Introduction to User Accounts and Groups


~~~bash
sudo useradd -m bill #Add a new user named bill -m option whcih creates a home directory for the bill user in the /home directory, if you forget this, they can't login. The -p option sets the password for the user.
~~~
~~~bash
sudo usermod -c "Phone 808-441-7862" bill #Add a comment to the bill account entry in the /etc/passwd file 
sudo usermod -aG students bill #Assign bill to the student, The -aG options adds a user to a group
groups jane #View all the groups that a user is in
sudo usermod -G teachers jane #Remove jane from the students group
groups dan #Verify that the user dan is now in the Staff group
sudo groupmod -n Staff admin #Rename the admin group to Staff
~~~

~~~bash 
sudo passwd bill #Change the password for bill
~~~
~~~bash
sudo userdel -r sally #deletes user sall, The -r option removes files in the user's home directory, and removes the home directory itself.
~~~
~~~bash 
sudo su #Change to the root user using sudo permissions
#su is the switch user command. su may be used to switch between any account, but defaults to the root account when no account is specified in the su command. Example syntax to switch to the bill account would be: sudo su bill
~~~
~~~bash
id bill # view detailed information about a particular user with the id
who #who is currently logged into this Linux
w #more detailed information on who is currently logged in
~~~
# Lab 08 Managing File Ownership and Permissions

~~~bash 
sudo chgrp share_access sharedrive/ #hange the group of the sharedrive directory to share_access
sudo chmod 770 sharedrive #Change the directory permissions to allow read, write, and execute permissions to only the owner and the group 
sudo chmod g+s sharedrive #Set the inherited group assignment bit (set-group-ID bit) on the sharedrive
#You may need to open and close ssh to reset permissions
~~~

# Lab 09 Introduction to Linux Shell Scripting
See line numbers in vi
~~~shell
:set nu
~~~
Don't forget `#!/bin/bash`.
Set perms to run script
~~~shell
chmod 755 directory_listing.sh
~~~
The $1 indicates the first parameter passed to the backup.sh script on the terminal line; $2 indicates the second parameter.

~~~shell
mkdir $1_$2
cp -a $1/. $1_$2

./backup.sh testproject 5-5-2020
~~~
`/backup.sh`: executes the backup.sh script.

`testproject`: assigns the text `testproject` as the `$1` argument used in the script as the directory to backup, and the first half of the name of the backup file that gets created.

`5-5-2020`: assigns the text `5-5-2020` as the `$2` argument used in the script as a date for the second half of the name of the backup file that gets created. You may use today's date if you wish.

### Example Script 

~~~shell
if [ $1 == '1' ]
then
  echo "The argument entered was 1"
  exit
fi

if [ $1 == '2' ]
then
  echo "The argument entered was 2"
  exit
else
  echo "The argument entered was not 2"
  exit
fi
~~~
The `$1` indicates the first parameter passed to the `logic.sh` script on the terminal line. Execute like:

~~~shell
./logic.sh 1
~~~