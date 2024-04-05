**Procedures/Commands**

- See below ports being configured (default interface range before applying):
```
Switch(config)# interface range fa0/1-4
Switch(config-if)# channel-group [#] mode [auto|desirable|on|active|passive]
Switch(config)# interface port-channel [#]
Switch(config-portchannel)# switchport mode trunk
Switch(config-portchannel)# switchport trunk allowed vlan [#, #]
```

- To load balance an EtherChannel see below (default method of load sharing uses the source MAC in frames:
```
Switch(config)# port-channel load-balance [src-mac|dst-mac|src-dst-mac|src-ip|dst-ip|src-dst-ip|src-port|dst-port|src-dst-port]
```

-  For verification use ``show etherchannel [summary|load balance|port-channel]``

**RULES**
- Matching Attributes: All interfaces in an EtherChannel must operate at the same speed and duplex settings to ensure consistency and proper load balancing.

- Uniform Port Types: The ports must be of the same type (e.g., all copper or all fiber) and support the same Ethernet standards to be eligible for grouping.

- Consistent Management Plane: Interfaces should belong to the same switch or be part of a single management domain, with the exception of stacked switches or Virtual Switching Systems (VSS) that act as a single entity.

- Configuration Uniformity: Across all ports, settings such as VLAN membership, Spanning Tree Protocol settings, and access or trunk mode must be uniform for the EtherChannel to function correctly.
