**Procedures/Commands**

- **Multicast Group:** A set of users receiving the same multicast transmission.
- **Source:** The originator of the multicast data stream.
- **Receiver:** An end-device interested in receiving a particular multicast stream.
- **Internet Group Management Protocol (IGMP):** Manages membership of hosts in a multicast group.
- **Protocol Independent Multicast (PIM):** The routing protocol used to direct multicast traffic between hosts.
- **Rendezvous Point (RP):** A router in PIM Sparse Mode which helps in connecting sources and receivers.
- **Multicast Distribution Tree:** The path that multicast traffic follows from the source to the receivers.

- See important information below:
```
Multicast MAC
01:00:5E:__:__:__
IPv4 = Class D (224.0.0.0 /4)
224.0.0.0 – 239.255.255.255
239.0.0.0 /8 – Limited Scope Multicast (Local)
```

- Enterprise Specific IP's are below:
```
Global Ranges
239.195.0.0/16 (FBNC)
239.47.0.0 - 239.47.127.255 (JCU)
Local Ranges
224.2.0.0 /16 (DVBRCS or UVDS)
224.4.0.0 /16 (UVDS)
224.10.0.0 /16 (UVDS)
224.47.0.0 /16 (Wave Control)
225.2.0.0 /16 (GBS)
227.147-150.0.0 /16 (Local HD)
227.47.0.0 /16 Local
```
- See simple multicast config example:
```
Router(config)# ip multicast-routing ENABLE GLOBALLY
Router(config)# ip pim rp-address 192.168.1.100 OR Router(config)# ip pim auto-rp listener DEFINE RENDEZVOUS POINT (REQUIRED FOR PIM SPARSE)
Router(config)# interface GigabitEthernet0/0 INTERFACES THAT WILL PARTICIPATE
Router(config-if)# ip pim sparse-mode
Router(config)# interface GigabitEthernet0/1 ENABLE IGMP ON INTERFACES TO OPTIMIZE
Router(config-if)# ip igmp join-group 239.1.1.1
```