## Linux Intro
### Uses
- Websites and Databases
- Workstations for businesses
- Desktops for home
- Arduino
- Raspberry Pi
- Smart Devices

### Distributions
- Core is known as a kernel
- Some distros come with software such as X Window

### Distros and Forks
#### Debian (apt)
  - Ubuntu
#### Fedora (yum)
  - RedHat
  - CentOS
  - Rocky
  - Fedora
  - Oracle Linux
#### SUSE ypp/dnf (rpm)
  - openSUSE
#### Arch Linux pacman(pkg)
  - Manjaro
  - ArchBang
#### Slackware pkgtools(pkg)
  - Zenwalk
  - Slax
  - VectorLinux
#### Gentoo portage(pkg)
  - Funtoo
  - Chrome OS
#### Independant
  - NixOS - 1 file for all configs
  - Solus - desktop focuses distro 
  - MX Linux - efficient desktop with simple config
  - Puppy Linux - extremely lightweight, runs from RAM
  - Void Linux - use of runit as init system,
  - Apline Linux - super stripped down for containers and server environments

## Linux Environment
#### Command Line Interpreter CLI
It is the command line, also referred to as the command line shell.
#### Linux Shells
- Bourne
- Bash (Bourne Again Shell)
- ZSH
- C Shell
- Korn

#### Linux GUI
- K Desktop Environment - KDE - BIG ONE
- GNOME - BIG ONE
- Pantheon
- Cinnamon
 **Red hat does not have a native GUI**

#### Multi-Tenant System
Linux was meant to be multi tenant. Can save money, add flexibility, and more efficient. Multiple users simultaneously work on one machines, using different terminals.

### Linux File Systems
A data management scheme design, consists of 3 parts. Logical structure is "file + directory + directory tree"
1. File system API - way to interact, adds read write and file management capabilities.
2. Data Information about the data management structure
3. Physical Storage of Data

**Every partition has its own file system.**
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/96b9e36e-be3a-4dee-8d0b-3d934ce2784a)

Partition Tables.

### Important File Systems

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/b747c877-8ed7-445e-9981-645c5587f99d)

- **/ (root)** - The root directory where the file system begins
- **/boot** - This is where the linux kernal and boot loader files are kept
- **/etc** - contains confix files for system
- **/bin** and **/usr/bin** contain most of the programs for the system
- **/sbin** and **/usr/bin** - contain programs for system administration by the super user
- **/usr** things that support user applications
- **/var** contains files that change as system is running
- **/lib** shared libraries
- **/home** user keeps personal work
- **/tmp** programs can write temp files
- **/dev** devices that are available to the system
- **/proc** entirely virtual and does not contain files
- **/media** used for mount points


### Key Features
- Mounting/Unmounting Partitions - normal users cannot access data on a partition or deleted device unless its been mounted
- Linux file naming - **case sensitive**, appending with . makes it invisible
- Filesystem Hierarchy Standard FHS - standard used by most distros, makes the distinction of sharable and un sharable files.




