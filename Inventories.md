**Procedures/Commands**

- Inventory file found at ``/etc/ansible/hosts``, can be named anything as long as it is referenced in the ``ansible.cfg`` file. 
  - Inventory file commonly written in INI-style or in YAML.
- To display inventory in yaml use ``ansible-inventory -i <inventory file> --list -y``
- Debugging triggers are below:
  - always: always trigger the debugger
  - never: never trigger the debugger
  - on_failure: trigger the debugger only if task failed
  - on_unreachable: trigger the debugger if the host is unreachable
  - on_skipped: trigger the debugger if the task is skipped
- Control nodes need the following to connect to managed hosts:
  - The location of the inventory file
  - The connection protocol to use (by default, SSH)
  - Whether a non-standard network port is needed to connect to the server
  - What user it can login as
  - If the user is not root, whether Ansible should escalate privileges to root
  - How Ansible should become root (by default, with sudo)
  - Whether to prompt for an SSH password to log in or a sudo password to gain privileges
- Settings to control SSH connection (go to [defaults] section):
  - ``remote_user`` specifies the user you want to use on the managed host (will use current if not prov.)
  - ``remote_port`` specifies what port sshd is using on the managed host (default is 22)
  - ``ask_pass`` controls whether Ansible will prompt you for SSH pwd (will not by default)
- Beginning of YAML inventory files must start with the following scaffolding structure:
```
{
  "_meta": {
      "hostvars": {}
   }
}
```
- Basic inventory structure using groups:
```
[all:vars] <- Apply to each host
domain_name=test.local

[routers] <- Group
lab08-red-router ansible_host=1.1.1.1
lab08-yellow-router ansible_host=2.2.2.2 

[routers:vars] <- Applies to all hosts in group
mgmt_int=Loopback0

[switches]
lab08-red-switch ansible_host=3.3.3.3
lab08-yellow-switch ansible_host=4.4.4.4

[switches:vars]
mgmt_int=Vlan1000
```