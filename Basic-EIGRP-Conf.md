**Procedures/Commands**

- Use ``show ip eigrp topology`` which will show:
     - Next hop address of successor, feasible distance, successor's reported distance, outbound interface to reach network

- Classic config below:
```
router eigrp 1 (MUST BE SAME AS PEER/NEIGHBOR)                                       
     passive-interface default (DISABLE ROUTING ON ALL INTERFACES)
     no passive-interface G0/0 (ENABLE ROUTING ON SPECIFIC INTERFACES)
     no auto-summary (DISABLE AUTO "CLASSFUL" SUMMARIZATION)
     network 192.168.10.0 (TELLS EIGRP WHICH INTERFACES ARE PARTICIPATING)
                              or
     network 192.168.10.0 0.0.0.255
```

- Show verification using ``show ip protocols``
- Verify neighbors using ``show ip eigrp neighbors``
- Verify packets using ``show ip eigrp traffic``
- Verify routing table using ``show ip route eigrp`` and ``show ip route``
- Verify topology using ``show ip eigrp topology``

- Configure named mode routing using example below:
```
route-tag notation dotted-decimal
router eigrp  <virtual instance name> (TSO REQUIRED FOR TAGGING BELOW)
     address-family ipv4 unicast autonomous-system <AS#> (NAMES DO NOT NEED TO MATCH)                                        
     network 192.168.10.0 0.0.0.255 (MUST BE THE SAME THROUGHOUT THE ENTIRE NETWORK)
     eigrp router-id <loopback0> (ASSIGN ROUTER ID, SHOULD BE LOOPBACK IP)
     eigrp default-route-tag <siteID> (TSO SITE ID X.X.X.X EG 901=9.0.1.0)
     af-interface default
     passive-interface (SETS ALL INTERFACES AS PASSIVE)
     af-interface G0/0
     no passive-interface (SETS INTERFACE AS ACTIVE WITHIN EIGRP)
```

**TROUBLESHOOTING STEPS**

- Must have matching Autonomous System Numbers 
- Must pass router authentication
- K-values must match
- IP MTU does not need to match
- Hello timers and hold timers do not need to match
