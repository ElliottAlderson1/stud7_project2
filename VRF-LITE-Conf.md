**How to's/steps**

- Create VRF using ``(config)# ip vrf RED``
- Assign to an interface using:
```
(config)#int g0/0/0
(config-if)#ip vrf forwarding RED
(config-if)#ip address 192.168.1.1 255.255.255.0
```
- Route over VRF's using ``(config)#router ospf 1 vrf RED``, this using OSPF but most protocols can use VRF's using a similar command
- Routing comparison example below:
```
EIGRP classic mode
DEV-R1(config)# router eigrp 10
DEV-R1(config-router)# address-family ipv4 vrf RED
DEV-R1(config-router-af)# autonomous-system 10
DEV-R1(config-router-af)# no auto-summary
DEV-R1(config-router-af)# network 10.1.1.0 0.0.0.255
DEV-R1(config-router-af)# eigrp stub connected

EIGRP named mode
DEV-R1(config)# router eigrp LAB
DEV-R1(config-router)# address-family ipv4 autonomous-system 10
DEV-R1(config-router)# address-family ipv4 vrf RED
DEV-R1(config-router-af)# network 10.1.1.0 0.0.0.255
DEV-R1(config-router-af)# eigrp stub connected

VRF static route
DEV-R1(config)# ip route vrf RED 10.10.50.0 255.255.255.0 GigabitEthernet0/0 
```
- Routing between VRF's example below:
```
interface vasileft1
 description JBN_VASI
 ip address 192.168.251.254 255.255.255.254
 ip access-group SSH_ALLOW_ACL in
 no keepalive
!
interface vasiright1
 description SOFU_VASI
 ip vrf forwarding SOFU
 ip address 192.168.251.255 255.255.255.254
 ip nat outside
 no keepalive
```
- VRF-LITE DHCP Config example below:
```
VRF specific pool
DEV-R1(config)# ip dhcp pool RED
DEV-R1(dhcp-config)# vrf RED
DEV-R1(config-int)# ip dhcp use vrf RED

global pool use
DEV-R1(config)# no ip dhcp use vrf connected
```
- Verify VRF EIGRP information using ``show ip eigrp vrf red neighbors``
- Show VRF ip routing table using ``show ip eigrp vrf red topology`` and ``show ip route vrf red``
- Send a ping to a VRF using ``ping 10.10.50.1 vrf red``