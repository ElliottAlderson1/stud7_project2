**How to steps/Procedure**

- Commands must be exactly the same as in the device's running-config:
```yaml
- name: Configure service
  ios_config:
    lines: <- (input one command here if only using one)
      - no service pad
      - service timestamps debug uptime
      - service timestamps log uptime
      - service password-encryption
```
- To assign configs to an individual interface, use parent:
```yaml
- name: Configure Uplink
  ios_config:
    parents: "interface GigabitEthernet0/1"
    lines: <- (input one command here if only using one)
      - description Uplink
      - ip address 192.168.0.1 255.255.255.0
```
- To input commands in a certain order:
```yaml
- name: ACL - ACL-IN
  parents: ["ip access-list extended ACL-IN"]
  commands:
    - permit tcp any any eq 22
    - permit tcp any any eq www
    - permit udp any any eq snmp
  match: exact
  replace: block
  before:
    - interface GigabitEthernet0/1
    - no ip access-group ACL-IN in
    - no ip access-list extended ACL-IN
  after:
    - interface GigabitEthernet0/1
    - ip access-group ACL-IN in
  notify: save configuration
```
- Use ``include`` statement to call upon outside templates, like Python modules:
```jinja
hostname {{ inventory_hostname }}
!
{% include 'dns_servers.j2' %}
!
{% include 'loopback_interfaces.j2' %}
!
logging host {{ syslog_server }}
!
line vty 0 4
  logging synchronous
  transport input ssh
  transport output ssh
  login local
```
- Pass SSH configs when running a playbook against IOS in the ``inventory`` file:
```jinja
[group_name:vars]
ansible_network_os=ios
ansible_user=orko
ansible_ssh_pass=P@ssw0rd123!
```
- Pass a filepath to the console through the ``src`` method instead of individually mapping using the ``commands`` line in a playbook:
```yaml
---
- name: PLAY 1 - DEPLOYING SNMP CONFIGURATIONS
  hosts: all
  connection: network_cli
  gather_facts: false

  tasks:
    - name: TASK 1 in PLAY 1 - ENSURE SNMP COMMANDS EXIST
      ios_config:
        src: ./configs/{{ enclave }}-snmp.cfg
```
- To backup a config set the ``backup:`` parameter in a task to ``true``
-  To define DHCP pools use:
```yaml
dhcp:

  excluded:
    - 22.47.1.254
    - 172.24.1.254

  pools:

    - name: LAB16_data
      network: 22.47.1.0 255.255.255.0
      default_router: 22.47.1.254

    - name: LAB16_voice
      network: 172.24.1.0 255.255.255.0
      default_router: 172.24.1.254
```