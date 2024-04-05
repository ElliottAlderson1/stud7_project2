* [Accessing your student VM from the Command prompt using SSH](#task-1-accessing-your-student-vm-from-the-command-prompt-using-ssh)
* [Managing user account group assignments](#task-2-managing-user-account-group-assignments)
* [Accessing directories and files based on groups and permissions](#task-3-accessing-directories-and-files-based-on-groups-and-permissions)

### Resources

* See instructional material

### Task 1 - Accessing your student VM from the Command prompt using SSH

#### Step 1 - Open the Command Prompt program on Windows

* Click in the Windows search bar at the bottom left of your student laptop, type `Command Prompt`, and click on the Command Prompt program to open it.
* Once the Command Prompt program opens, click inside it's window.

#### Step 2 - Remotely connect to your Student Virtual Machine(VM) using SSH

* Enter the SSH commands into the Command Prompt program using `your` student number and student VM IP address:

  ```shell
  ssh <your_student#>@<student_vm_ip_address>
  ```
* Press `enter`.
* When prompted, enter your student password for the student VM:

  ```shell
  <your_student#>@<student_vm_ip_address> password:
  ```
* Press `enter`.
* If login was successful, you will see a new prompt similar to the one below:

  ```shell
  [<your_student#>@<student_vm> ~]$
  ```

### Task 2 - Managing user account group assignments

#### Step 1 - Create new user account

* Create a new user named `beth`using sudo permission:

  ```shell
  sudo useradd -m beth
  ```
* Assign a password to the `beth` user account using sudo permission:

  ```shell
  sudo passwd beth
  ```
* When prompted, enter the password `supersecret`.
* Create a new user named `greg`using sudo permission:

  ```shell
  sudo useradd -m greg
  ```
* Assign a password to the `greg` user account using sudo permission:

  ```shell
  sudo passwd greg
  ```
* When prompted, enter the password `supersecret`.
* Verify that the users wer created by viewing the last 5 lines of the `/etc/passwd` file:

  ```shell
  tail -5 /etc/passwd
  ```

  > You should see an entry for each of the two recently created users "beth", and "greg".

#### Step 2 - Create a new group

* Create a new group named `share_access` using sudo permission:

  ```shell
  sudo groupadd share_access
  ```
* Verify that the `share_acces` group was created:

  ```shell
  tail -5 /etc/group
  ```
* You should see:

  ```shell
  ...
  share_access:x:1011:
  ```

  > Your group ID may be different than the `1011` you see in this example.

#### Step 3 - Add users to a group

* Add the user `greg` to the `share_access` group using sudo permission:

  ```shell
  sudo usermod -aG share_access greg
  ```
* Add your student user to the `share_access` group using sudo permission:

  ```shell
  sudo usermod -aG share_access <student_user_account>
  ```
* Verify that your student user account and the `greg` user account are in the `share_access` group:

  ```shell
  cat /etc/group | grep share_access
  ```
* You should see:

  ```shell
  share_access:x:1011:greg,student1
  ```

  > Your output may be slightly different, but you should see two users assigned to the `share_access` group.

### Task 3 - Accessing directories and files based on groups and permissions

#### Step 1 - Create a shardrive in the /home directory

* Navigate to the go to the Linux system `/home` directory:

  ```shell
  cd /home
  ```
* Verify that you are in the Linux system `/home` directory:

  ```shell
  pwd
  ```
* You should see:

  ```shell
  /home
  ```
* Creat a new dirctory to be used as a `sharedrive` between users using the sudo permission:

  ```shell
  sudo mkdir sharedrive
  ```
* View the new `sharedrive` directory listing:

  ```shell
  ls -l
  ```
* You should see:

  ```shell
  ...
  drwxr-xr-x.  2 root  root  6 May  9 08:00 sharedrive
  ...
  ```

  > Notice that the directory permissions are set to: Owner wrx, Group r-x, Other r-x. Also notice that the owner is root, and the group is root. At this point, only the root account can change anything in this file. We're going to change that.

#### Step 2 - Edit the permissions, and group of a directory

* Change the group of the `sharedrive` directory to `share_access`:

  ```shell
  sudo chgrp share_access sharedrive/
  ```
* Change the directory permissions to allow read, write, and execute permissions to only the owner and the group assigned to the `sharedrive` directory using sudo permission:

  ```shell
  sudo chmod 770 sharedrive
  ```
* Set the inherited group assignment bit (`set-group-ID bit`) on the `sharedrive` directory using sudo permission:

  ```shell
  sudo chmod g+s sharedrive
  ```

  > This option forces every file or directory made in the `sharedrive` directory to have the same initial group (share_access) as the `sharedrive` directory itself. This will allow anyone in the `share_access` group to read, write, and execute any directory or file in the `sharedrive` folder.
* View the new permissions on the `sharedrive` listing:

  ```shell
  ls -l
  ```
* You should see:

  ```shell
  ...
  drwxrws---.  2 root   share_access   6 May  9 08:09 sharedrive
  ...
  ```

  > `d` indicates this is a directory. `rwxrws---` indicates that owners have read/write/execute permissions, group members have read/write/execute/set-group-id bit permissions, and other users have no permissions.

#### Step 3 - Create a directory as the owner of the directory with different group permissions

* Change into the `sharedrive` directory:

  > **NOTE** if you do not have permissions to enter this directory, close and reopen your ssh session.
* Create a new directory `reports`

  ```shell
  mkdir reports
  ```

  > Notice that you did not need to use sudo permission to create this directory. This is because your student user account is in the `share_access` group which has write pwermissions on this directory.
* View the group assingment of the new directory:

  ```shell
  ls -l
  ```
* You should see:

  ```shell
  drwxrwsr-x. 2 student1 share_access 6 May  9 08:35 reports
  ```

  > Notice that the `reports` directory is assigned to the `share_access` group. Your output will have your student number as the owner.

#### Step 4 - Create a file as the owner of the file with different group permissions

* Change into the `reports` directory:

  ```shell
  cd reports
  ```
* Create a file file1:

  ```shell
  echo "Text added by student user" > file_1.txt
  ```
* View the group assingment of the new file:

  ```shell
  ls -l
  ```
* You should see:

  ```shell
  -rw-rw-r--. 1 student1 share_access 27 May  9 08:41 file_1.txt
  ```

  > Notice that the `file_1.txt` file is assigned to the `share_access` group. Your output will have your student number as the owner.

#### Step 5 - Fail to access a directory because a user is not in the required group

* Change back to the `/home` directory:

  ```shell
  cd /home
  ```
* Switch to the user `beth`:

  ```shell
  su beth
  ```

  > When prompted, enter the password you set for `beth` which should be: `supersecret`
* Attempt to access the `sharedrive` directory:

  ```shell
  cd sharedrive
  ```
* You will see:

  ```shell
  bash: cd: sharedrive/: Permission denied
  ```

  > You are receiving this message because the `beth` user account is not the owner of the `sharedrive` directory, nor is the `beth` account in the `share_access` group assigned to the `sharedrive` directory. Because of this, `beth` cannot access the `sharedrive` directory.

#### Step 6 - Access a directory because of a user's assignment to the required group

* Switch to the user `greg`:

  ```shell
  su greg
  ```

  > When prompted, enter the password you set for `greg` which should be: `supersecret`.
* Attempt to access the `sharedrive` directory:

  ```shell
  cd sharedrive
  ```

  > This time you should have no problems accessing the `sharedrive` directory because `greg` is in the `share_access` group.

#### Step 7 Create a file in a folder not owned by the new file's creator

* Create a new file named `file2` using the `nano` text editor program:

  ```shell
  nano file_2.txt
  ```
* In `nano`, add the following text to the `file_2.txt` file:

  ```shell
  This is file 2
  ```
* Save your changes to the `file_2.txt` file by holding down the `ctrl` key and pressing the `o` key.
* When prompted with: `"File Name to Write: file_2.txt"`, press `enter`.
* Exit `nano` by holding down the `ctrl` key and pressing the `x` key.
* View the group assingment of the `file_2.txt` file:

  ```shell
  ls -l
  ```
* You should see:

  ```shell
  -rw-rw-r--. 1 greg     share_access 14 May  9 10:51 file_2.txt
  drwxrwsr-x. 2 studx share_access 19 May  9 08:41 reports
  ```

  > Notice that the `file2` file is owned by the `greg` user, and assigned to the `share_access` group.

#### Step 8 - Edit a file that you are not the owner of, but have access to because of group permissions

* Change to the `reports` directory:

  ```shell
  cd reports
  ```
* Open the `file_1.txt` file with `nano`:

  ```shell
  nano file_1.txt
  ```
* Add the following text below the existing test:

  ```shell
  Text added by greg user
  ```
* Save your changes to the `file_1.txt` file by holding down the `ctrl` key and pressing the `o` key.
* When prompted with: `"File Name to Write: file_1.txt"`, press `enter`.
* Exit `nano` by holding down the `ctrl` key and pressing the `x` key.
* Verify that the changes to `file_1.txt` were saved:

  ```shell
  cat file_1.txt
  ```
* You should see:

  ```shell
  Text added by student user
  Text added by greg user
  ```