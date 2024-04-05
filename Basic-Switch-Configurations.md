**Useful Files**

- [Basic_Switch_Conf.txt](uploads/bf13024010a810a1d2766cb5348bee92/Basic_Switch_Conf.txt)
- [Basic_Access_Port.txt](uploads/360218abe74d45c9c510f9ff848121b2/Basic_Access_Port.txt)
- [Basic_Trunk_Port.txt](uploads/e2beb23a42743978be89b060a285e0a4/Basic_Trunk_Port.txt)
- [Basic_VLAN_Conf.txt](uploads/d68a6b6de838022c28850339c9ee47b5/Basic_VLAN_Conf.txt)

- Basic access port config below:
```
Switch(config)# interface FastEthernet 1/0
Switch(config-if)# description DATA/VOICE
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan <data vlan>
Switch(config-if)# switchport voice vlan <voice vlan>
```

- Basic trunk port config below:
```
Switch(config)# interface FastEthernet 0/1 
Switch(config-if)# switchport mode trunk 
Switch(config-if)# switchport trunk native vlan 888
Switch(config-if)# switchport trunk encapsulation dot1q 
Switch(config-if)# switchport trunk allowed vlan [add | remove] <vlan-id>
Switch(config-if)# switchport trunk allowed vlan remove 1,166 
Switch(config-if)# switchport nonegotiate 
```