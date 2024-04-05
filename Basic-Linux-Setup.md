**Initial Setup Process**
 
  ***Whenever setting up a new instance***
- Install Ansible ``sudo dnf install ansible -y`` 
- View version information ``ansible --version`` 
- Install Paramiko``pip3.11 install paramiko --user`` ***Mandatory Ansible package***
- Install required library ``pip install --user ansible-pylibssh`` 
- To generate an ssh config file, do the following steps:
  1. ``touch config`` in /.ssh directory
  2. ``sudo chmod 644 config`` changes the permissions to standard OpenSSH permission level
  3. Add the following code to the config file:
```
Host * #All Hosts
  StrictHostKeyChecking no
  UserKnownHostsFile=/dev/null
```
- To disable host key checking for Ansible use the following steps:
  1. ``cd ~`` cd to home directory
  2. ``sudo nano /etc/ansible/ansible.cfg`` to access config file
  3. Add the following code:
```
[defaults]
host_key_checking=False
```
- Set up SSH for w/o pwd using:
```
$ ssh-agent bash
$ ssh-add ~/.ssh/id_rsa
```
- When connecting you can use ``--ask-become-pass`` to prompt for a password
- Can use the following code to specify pem files:
```
$ ssh-agent bash 
$ ssh-add ~/.ssh/keypair.pem 
```
- Add private key without using ssh-agent using ``aws_host ansible_ssh_private_key_file=/home/example/.ssh/aws.pem``
- Ad hoc commands are run from ``/usr/bin/ansible`` which is a tool to automate a single task
  - Syntax: ``ansible <hosts> [-m <module_name>] -a <"arguments"> -u <username> [--become]``
    - ``module_name`` is an optional parameter, like ``shell``, ``yum``, ``apt``, ``file``, etc
    - ``arguments`` are passed in relation to the module through ``key=value`` or JSON string ``{}``
    - ``username`` specifies the user for Ansible to execute commands
    - ``become`` is optional when needed to use ``sudo`` privileges, false by default
  - Managing services syntax examples:
    - ``ansible webservers -m service -a "name=httpd state=started"`` to ensure a service is started
    - ``ansible webservers -m service -a "name=httpd state=restarted" to restart a service
    - ``ansible webservers -m service -a "name=httpd state=stopped"`` ensures service is stopped
  - ping all hosts using ``ansible all -m ping``
  - Gather facts (discovered variables in a system) using ``ansible all -m setup``
- Reboot a host with parallel forks using ``ansible <name> -a "/sbin/reboot" -f 10``
- Ensure package is installed w/o installing use ``ansible webservers -m ansible.builtin.yum -a "name=acme state=present"``
- Create, manage and remove user accounts using ``ansible all -m ansible.builtin.user -a "name=foo password=<crypted password here>“``
- To use check mode to see changes use ``ansible all -m copy -a "content=foo dest=/root/bar.txt" -C``