**Procedures/Commands**

- To check for if switch is root bridge use ``show spanning-tree`` and look for ``root``
- Place a root bridge using VLANs using the below example:
```
CS1(config)# spanning-tree vlan 10,20,30 priority 4096

\\OR\\
		    
CS1(config)# spanning-tree vlan 10,20,30 root primary
CS2(config)# spanning-tree vlan 10,20,30 root secondary
```

- To make a port update as fast as possible use ``spanning-tree portfast``
     - On trunks use ``spanning-tree portfast trunk``
- To ensure a switch isn't plugged into an access port (don't use on a trunk) use ``spanning-tree bpduguard enable``