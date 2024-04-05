**Procedures/Commands**

- Interface configuration below:
```
HQ(config)# interface Tunnel233
HQ(config-if)#description TO_BRANCH
HQ(config-if)#ip address 192.168.100.1 255.255.255.252
HQ(config-if)#tunnel source FastEthernet0/0
HQ(config-if)#tunnel destination 192.168.23.3

\\OTHER END\\

Branch(config)# interface Tunnel121
Branch(config-if)#description TO_HQ
Branch(config-if)#ip address 192.168.100.2 255.255.255.252
Branch(config-if)#tunnel source FastEthernet0/0
Branch(config-if)#tunnel destination 192.168.12.1
```

- Use ``Router(config-if)# keepalive <seconds> <retries>`` to allow the router at the tunnel source to determine if dest. tunnel is down
- Maximum Transmission Unit (MTU) size for an Ethernet link is ``1500``
- ``ip tcp mss-adjust`` is used to avoid any packet fragmentation from initial TCP handshake

- See below for advanced GRE tunnel config:
```
Site(config)# interface Tunnel 1001
Site(config-if)#description TO_HUB
Site(config-if)# bandwidth 10000		[Bandwidth statement used by routing protocols to determine route metric]
Site(config-if)# ip unnumbered Loopback0	                        [Used instead of IP address and must be routable]
Site(config-if)# ip mtu 1400
Site(config-if)# ip pim sparse-mode		   		                          [Used for multicast purposes]
Site(config-if)# ip tcp adjust-mss 1360		                              [Used to set max TCP segment size]
Site(config-if)# delay 4000		    [Delay statement used by routing protocols to determine route metric]
Site(config-if)# keepalive 10 3	     [Tunnel will be in a down state if destination is unreachable for 30 seconds]
Site(config-if)# tunnel source FastEthernet 0/0
Site(config-if)# tunnel destination 192.168.100.1
Site(config-if)# service-policy output {name}				   	      [Used for QOS purposes]
Site(config-if)# ip route 192.168.100.0 255.255.255.252 192.168.200.1  [Static route to distant end Encryptor network]
```

- Verification commands include ``show interface tunnel ###``, ``show ip interface brief``, ``show interface description``
- Determine MTU sizing using a ping sweep shown below (Windows ping overhead 28 bytes (20 for IP header, 8 for ICMP header) Eg ping –f –l 1472 works, 1473 does not.):
```
R2#ping
Protocol [ip]:   
Target IP address: 192.168.12.1
Repeat count [5]: 1
Datagram size [100]: 
Timeout in seconds [2]: 
Extended commands [n]: y
Source address or interface: 
Type of service [0]: 
Set DF bit in IP header? [no]: y
Validate reply data? [no]: 
Data pattern [0xABCD]: 
Loose, Strict, Record, Timestamp, Verbose[none]: v
Loose, Strict, Record, Timestamp, Verbose[V]: 
Sweep range of sizes [n]: y
Sweep min size [36]: 1495
Sweep max size [18024]: 1505
Sweep interval [1]: 
Type escape sequence to abort.
Sending 11, [1495..1505]-byte ICMP Echos to 192.168.12.1, timeout is 2 seconds:
Packet sent with the DF bit set
Reply to request 0 (1 ms) (size 1495)
…
Reply to request 5 (4 ms) (size 1500)
Request 6 timed out (size 1501)
…   <----------
Success rate is 54 percent (6/11), round-trip min/avg/max = 1/2/4 ms
```
![Tunnel_Ex](uploads/be039758ec7c4afc1581522336127f0e/Tunnel_Ex.png)
