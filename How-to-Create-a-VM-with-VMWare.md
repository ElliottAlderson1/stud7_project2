## In ESXi
Connect to host on the web browser with ip `10.10.41.1`.

Find  `Create / Register VM` button by right clicking `Virtual Machines`, select `creation type` and `Create a new virtual machine`.

### Select Name, OS, storage
Enter a VM name. `Compatibility` should match the ESXi using, also the default. We use `Linux` and `Rocky Linux (64-bit)`. Select the storage with your student number `ESXxx_NVMe`.

### Custom Hardware
Select CPU, RAM, Storage.
- `CPU`  `4`
- `Memory` `4096 MB`
- `Hard disk 1` `50 GB`
#### For provisioning: 
Select in drop down menu.
1. Thick Provision Lazy Zeroed (Default) 
2. Thick Provision Eager Zeroed
3. Thin Provision `select this one`

### More Custom Hardware

- `Network Adapter 1` to `VM Network` and select `Connect`
- Set `DVD/CD Drive 1` to `Datastore NVMe_ISOs file`
- In the `Datastore` browser window, click on `ISOs` folder, open the Rocky Linux folder, use `.iso` file `Rocky-8-9-x86_64-dvd1.iso`, and click `Select` in the bottom right.
-  Ensure the `"Connect"` box next to the `Datastore ISO file` is checked.
- Click `next`, check over configs, and then check `finish`

### Access
Power on VM, open `Console` `open browser console`. Select `Install Rocky Linux 8` and press enter. Select English.

### Installation Destination
Sometimes just select automatic and done.

For storage config select `custom` (for security), in installation destination, under summary page. On the Manual Partitioning page, click `Click here to create them automatically`. Usually leave as default.

> The screen will display what the default storage configuration would be. /, /boot/efi, and /boot are required.

> Security Policies: If we were applying the DISA STIG Security Policy, Additional mounts would need to be created for the following directories: /tmp, /var, /var/log, /var/tmp, and /var/log/audit.

> Kubernetes: If you plan on using the device for Kubernetes Version 1.21 or earlier the mount for swap can be removed here.  

### Configure Network and Host Name
`Installation Summary` page, click on `Network & Host Name`. Enter host name. Select the `configure` button in the bottom right. In the IPv4 Settings tab, change the Method to `Manual`, and select the `Add` button in the Addresses block.

Enter the following:

- IPv4 address: 172.16.<student#>.10
- Network mask: 255.255.255.0
- Gateway: 172.16.<student#>.254
- DNS: 10.200.99.30 & 31
- Leave `Search domains` blank
- Enter two DNS servers with comma

Move to the IPv6 Settings tab and change the method to `Disabled`.

Save and Change the switch at the top right from `off` to `on`.

### Configure Software Selection
`Installation Summary` page - `Software Selection`. 

Base Environment select `Server`.

In the section: Additional software for Selected Environment Select:
- Network File System Client
- Development Tools
- Headless Management
- RPM Development Tools
- System Tools

> These tools installed should be able to give you everything you need to troubleshoot issues in an Air-Gapped environment.

### Configure the Security Policy
select the option named `DISA STIG for Red Hat Enterprise Linux 8`. You can remove the policy here too by selecting `OFF`.

### Configure the Root Password
In the Installation summary page.

### Configure the User Creation 
In the Installation summary page. Make sure to make `administrator`.

### Final Steps
Click `Begin Insallation`, it should take a while. When prompted select `Reboot System`.

## Verifying Installation & Troubleshooting
View the Anaconda Kickstart file.

~~~bash
sudo cat /root/anaconda-ks.cfg
~~~

### Network Config

~~~bash
ip address #Display the connection status and IP address
ip neighbor show #Check ARP table for connection to the gateway
ping <gateway-ip> #Ping the gateway or another device on the network
~~~

### NetworkManager
#### Network Manager Text User Interface
~~~bash
sudo nmtui
~~~
Any time you make a change to NetworkManager, you must restart the NetworkManager service to ensure the changes are configured.
~~~bash
sudo systemctl restart NetworkManager.service
~~~
Or use cli
~~~bash
sudo man nmcli
~~~
### View Hostname Config
~~~bash
sudo cat /etc/hostname #need to reboot if changed
~~~
Set with, no need to rebood, but open a new shell session
~~~bash
sudo hostnamectl set-hostname <new-hostname>

hostnamectl

su <username>
~~~
### View the DNS Configs
~~~bash
sudo cat /etc/resolv.conf
~~~
### View the drives, partitions, and LVMs configuration
If you add new drives, and to mount automatically, you need them to be added here. Also `swap` is here which should be removed for kubernetes.
~~~bash
sudo cat /etc/fstab
lsblk #view block storage, the size of the disk, the type, and the mount point of partitions or LVMs
sudo lvdisplay # view more detailed about LVM
df -h # show the total space and available space on all partions -h is for human readable
~~~

### View & update installed packages
~~~bash
sudo cat /etc/fstab
yum list installed
sudo yum update -y
~~~


### Verify client-side Network Time Protocol (NTP)
~~~bash
chronyc sources #View the NTP sources configured
chronyc tracking #View the time on your server
systemctl chronyd
~~~

## Editing the NTP configurations
~~~bash
sudo nano /etc/chrony.conf
~~~
Remove pool and add local server like:
~~~bash
server 44.44.44.10 iburst #comment into file
~~~
You must restart and check after this
~~~bash
systemctl restart chronyd.service
~~~

Update all software
~~~bash
sudo yum update -y
sudo dnf update -y
~~~

Then take a snapshot.

