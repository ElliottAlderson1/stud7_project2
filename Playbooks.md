**Useful links**

https://strftime.org/ 

**Procedures/Commands**

- While you might run the main ``/usr/bin/ansible`` program for ad-hoc tasks, playbooks are more likely to be kept in source control and used to push out your configuration or assure the configurations of your remote systems are in spec
- Keyword set defaults for objects inside rather than objects themselves:
  - name: ``-name: Disable CDP``
  - hosts: ``hosts: red_devices``
  - connection: ``connection: network_cli``
  - gather_facts: ``True`` or ``False``, gather useful variables about remote hosts that can be used in playbooks
  - handler: defines the next action if there is any change made to the host after completion of any tasks that has a ‘notify’ attribute associated with it
  - become = Boolean that controls if privilege escalation is used or not on Task execution
    - ``become_user`` = User that you "become" after using privilege escalation
    - ``become_method`` = Method of privilege escalation to use (such as sudo or su)
- Anatomy example:
![playbook1](uploads/c912614d4d9623da4988f27504ac5bae/playbook1.png)
- Rules about naming variables inside a playbook:
  - Begins with uppercase or lowercase, cannot start with underscore, space, digit, or special char.
  - Should only contain alphanumeric characters, underscores, and integers
  - Some reserved keywords cannot be used (Python and Ansible keywords)

![variable_names](uploads/e59a5b330d3e8eee2edcb945d0852a10/variable_names.png)
- Ansible has 3 main scopes:
  - ``Global`` which the value is set for all hosts
  - ``Hosts`` which the value is set for a particular host (or group)
  - ``Play`` which the value is set for all hosts in the context of the current play
- ``inventory_hostname`` is built-in and takes the hostname of machine from inventory or config file
- ``ansible_hostname`` is built-in and holds hostname of remote host like ``inventory_hostname``
  - Difference is that ``ansible_hostname`` takes hostname of remote machine from facts collected during ``gather_facts`` section of playbook
- Something to note:
```
hostvars is a dictionary which has an entry for each inventory host. If you want to access host information, 
you need to use the inventory_hostname. If you want to use/print the name of the host as configured on the host, 
you should use ansible_hostname since most likely the IP will be used in the inventory file.
```
- ``inventory_dir`` stores the absolute path for inventory file used by playbook
- ``playbook_dir`` is the path for the directory of current playbook being executed
- Using the debug module example:
```yaml
---
- name: Debug Variables
  hosts: all
  gather_facts: false
  connection: local

  tasks:
    - name: Debug MGMT
      debug:
        var: mgmt_int 
```
- To run a playbook use ``ansible-playbook <playbook_name> -i <inventoryfile_name>``
  - To pass variables you can use ``ansible-playbook <playbook>.yml -e <variable>=<value>``
  - To pass multiple variables you can use ``ansible-playbook <playbook>.yml -e "<variable>=<value> <variable>=<value>"``
  - Can create a ``.yml`` file that defines variables (varible: value) then call upon it in playbook:
```yaml
---
- name: Debug variables
  hosts: localhost
  gather_facts: false
  connection: local
  vars_files:
    - my_vars.yml

#CAN ALSO STATICALLY DEFINE
  vars:
    variable: value
    variable: value
```
- Reference a name and variable and print a value using the below example:
```yaml
    - name: DEBUG AND PRINT THE MANAGEMENT INTERFACE
      debug: 
        msg: "The management interface for {{ inventory_hostname }} is {{ mgmt_int }}."
```
- To only run for one device add ``run_once: true`` to playbook task definition
- Nest groups within themselves using the following structure:
```yaml
[all:children]
<group_name> <- Creates parent group

[<group_name>:children]
routers <- Groups previously defined
switches
riverbeds
```
- See structure by debugging ``group`` special variable:
```yaml
    - name: DEBUG AND PRINT GROUPS
      debug: 
        var: groups
      run_once: true
```
- Debug Ansible version:
```yaml
    - name: DEBUG AND PRINT ANSIBLE_VERSION
      debug: 
        msg: "Ansible Version: '{{ ansible_version }}'"
      run_once: true
```
- To influence host variables and group variables, you can create ``host_vars`` and ``group_vars`` directories in the parent directory where playbook and inventory files are stored and make ``.yml`` or ``.json`` files which will automatically map 
- Use the ``register`` task option to save the output of a task to a variable, example:
```yaml
    - name: Pull tenants from Nautobot
      uri:
        method: GET
        url: https://demo.nautobot.com/api/tenancy/tenants
        headers:
          Content-Type: application/json
          Accept: application/json
          Authorization: Token aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
        validate_certs: false
      register: nautobot_tenants

    - name: Debug nautobot tenants
      debug:
        var: nautobot_tenants
```
- In the above tasks, you can use the ``count`` notation since the ``.json`` is a dictionary using the ``nautobot_tenants.json.count`` or the ``nautobot_tenants['json']['count']``
- You can also use ``nautobot_tenants.json.results[0]`` to pull the first indexed item from the list
- To display a list of vars that have a certain attribute use:
```yaml
    - name: GET ELEMENTS THAT HAVE A TRUE VALUE FOR STATUS AS A LIST
      debug:
        var: variable_name | selectattr("status") | list
```
- To display a certain attribute from a variable, such as a list of names:
```yaml
    - name: RETURN LIST OF ALL NAME KEYS IN THE VARIABLE_NAME LIST OF DICTIONARIES
      debug:
        var: variable_name | map(attribute="name") | list
```
- Can swap a value for another value using the built-in Python ``ternary`` operator:
```yaml
    - name: CONVERT BOOLEAN T/F TO SOMETHING MORE CONTEXTUAL FOR NETWORKING
      debug:
        var: interface_state | ternary("up", "down")

    - name: CONVERT BOOLEAN T/F USING PROGRAMING LOGIC
      debug:
        msg: "{{ 'up' if interface_state else 'down' }}"
```
- To apply templates and make directories using a task:
```yaml
---
- name: Test Templates
  hosts: lab16_routers
  gather_facts: false
  connection: local

  tasks:

    - name: Create Configs Directory
      file:
        path: configs
        state: directory

    - name: Test DHCP Template
      template:
        src: dhcp.j2
        dest: "./configs/{{ inventory_hostname }}.cfg"
```
- Use the ``--ask-become-pass`` command when using ``become`` to pass the sudo password