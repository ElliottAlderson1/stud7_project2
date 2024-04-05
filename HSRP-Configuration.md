**Procedures/Commands**

- Rides ``vlan 1`` so it must be enabled on trunk between two layer 3 devices
- Use ``standby [group-number] ip [ip-address]`` to configure the HSRP virtual IP address
     - Virtual IP address must be identical on all routers in HSRP group
     - Host devices in same network should be config'd with a default gateway IP matching virtual IP address
     - HSRPv1 group numbers = 0-255
     - HSRPv2 group numbers = 0-4095
     - Can assign priority values, default is 100. If a tie occurs router with highest IP wins
```
CS1(config)# interface vlan 10
CS1(config-if)# ip address 10.1.1.253 255.255.255.0
CS1(config-if)# standby v 2
CS1(config-if)# standby 10 ip 10.1.1.254
CS1(config-if)# standby 10 preempt (ensures config'd device will be the active router as long as active and sending hellos)
```

- Verify using ``show standby`` and ``show standby brief``

**HSRP CONFIG WITH IP SLA AND TRACKING**

- Core Switch 1
```
CS1(config)#ip sla 1
CS1(config-ip-sla)#icmp-echo 20.20.20.25 source-ip 20.20.20.26
CS1(config-ip-sla-echo)# frequency 10
CS1(config)# ip sla schedule 1 life forever start-time now

CS1(config)# track 1 ip sla 1 reachability
CS1(config-track)# delay down 20 up 40

CS1(config)# interface vlan 10
CS1(config-if)# ip address 10.1.1.253 255.255.255.0
CS1(config-if)# Standby v 2
CS1(config-if)# standby 10 ip 10.1.1.254
CS1(config-if)# standby 10 priority 110
CS1(config-if)# standby 10 preempt
CS1(config-if)# standby 10 track 1 decrement 80
```

- Core Switch 2
```
CS2(config)#ip sla 1
CS2(config-ip-sla)#icmp-echo 20.20.20.29 source-ip 20.20.20.30
CS2(config-ip-sla-echo)# frequency 10
CS2(config)# ip sla schedule 1 life forever start-time now

CS2(config)# track 1 ip sla 1 reachability
CS2(config-track)# delay down 20 up 40

CS2(config)# interface vlan 10
CS2(config-if)# ip address 10.1.1.252 255.255.255.0
CS2(config-if)# Standby v 2
CS2(config-if)# standby 10 ip 10.1.1.254
CS2(config-if)# standby 10 preempt
CS2(config-if)# standby 10 track 1 decrement 80
```