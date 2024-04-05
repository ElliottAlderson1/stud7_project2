## Protocols
Set of rules governing communications and data. Manage control of data and access control of a link being shared. Two models (OSI & TCP/IP) The following types:

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/cb8cbaf2-f711-477a-9ee5-b680446eb548)

### 1.  Network Communications Protocol
- Hypertext Transfer Protocol (HTTP) communication of internet and server client relations
- Transmission Control Protocol (TCP) handshake packets
- Internet Protocol (IP) routing packets across networks
- User Datagram Protocl (UCP) - does not ensure connection
- File Transfer Protocol (TCP)

**Fill IN**
Calling Layer number is usually OSI (usually teaching). Calling it by name is TCP/IP and usually in practice.

### DNS
Domain Name System is not same as Services. DNS is a protocol. Can use Windows DNS Server component of Microsoft DNS. BIND is the most popular DNS server. Primary done by DNS query and DNS lookup. Other open source DNS:
- CoreDNS
- BIND
- PowerDNS
- NLnet Labs Server Daemon

### Networking Services
Systems use IP addresses to communicate across networks. Some systems hold multiple IP depending on number of interfaces to communicate.
#### Linux
- `/etc/hosts` - local file that maps hostnames to ip address
- `/etc/resolv.conf` configure DNS server and search domains
- `/etc/nsswitch.conf`

To view ip address configured in Linux, use the `ip address show` command. It shows `lo` which is the loop back for internal use. It also shows `eth0` which is primary communication interface. In the case of class lab its is often `ens34`.

Can also use the `systemctl status NetworkManager` to see more data.

If you need to add an IP address or forgot during initial setup can use the ip address command. `<int>` would be an interface like `eth0` or `ens34`.

~~~bash
sudo ip address add 192.168.2.20/24 dev <int>
~~~

Can test connectivity with `ping`, can use for tracking and isolating hardware and software. Determining status of the network and hosts, testing measuring networks.

### DNS Client
DNS client servers is used to resolve DNS domain names.
Top Level, or the root domain, then followed by the vendor name under a register level (.com .net .edu). Web browser gets rid of the root dot for you.

First your computer looks in local cache. If it cannot find it, it sends to local DNS server, if it does not have it sends a recursive query to contact root domain server. The recurserver will contact the Top Level Domain (TLD) Server. The recursive server will go to the authoritative server.

### NetworkManager
a standard Linux network configuration tool suite. It updates the `/etc/resolve.conf` file with DNS settings from NetworkManager connection profiles. You can manually configure this too. Uses nmtui, GUI, and nmcli.
- `nmcli` command line tool to script and interact with Network Manager
- `nmtui` a curses-based text user interface
- `Nm-connection-editor` a graphical user interface for certain tasks
- `Control-center` a graphical interface from GNOME shell
- `Network connection icon` another GUI from GNOME shell representing network connection states as reported by NetworkManager.

To check status, to start, or to enable at boot
~~~bash
systemctl status NetworkManager
systemctl start NetworkManager
systemctl enable NetworkManager
~~~



To start/stop services uses the commands 
~~~bash
sudo systemctl start NetworkManager.service
sudo systemctl stop NetworkManager.service
sudo systemctl restart NetworkManager.service
~~~

You can also use nmcli to start stop on Rocky 8.
~~~bash
sudo nmcli networking off
sudo nmcli networking on
~~~





