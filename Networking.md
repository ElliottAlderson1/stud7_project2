**Commands:**

- **sudo ip address add < ip address >< subnet mask > dev < interface name >:** adds an ip address to an existing interface (use _del_ in place of add to remove an ip address)
- **sudo nano /etc/hosts:** opens hosts file for editing
- **sudo nano /etc/resolv.conf:** opens dns resolv file for editing
- **Network Manager:**
     - **nmtui:** deploys Network Manager
     - **nmcli:** allows for quickly configuring without screen
     - **systemctl status NetworkManager:** checks the status of NetworkManager
     - **systemctl start NetworkManager:** start NetworkManager
     - **systemctl enable NetworkManager:** enable NetworkManger at boot
     - **nmcli dev status:** shows devices and their status w/ connection interface
     - **sudo ip link set lo down**: shuts down loopback address
- **sudo firewall-cmd --add-port=80/tcp --permanent:** For this example is 80, this enables a port on the firewall
     - **sudo systemctl restart firewalld:** Restarts firewall after changes have been made