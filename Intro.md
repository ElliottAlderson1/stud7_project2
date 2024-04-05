**How to/Steps**

- Plays are the elements that tie tasks to the servers where they'll run.
```
---
name: Update web servers    play name
      hosts: webservers                   servers it will be run on.
…
```
- Plays can be consolidated into playbooks:
```
--- 
name: Update web servers
      hosts: webservers 
       remote_user: root 
               tasks: 
         - name: Ensure apache is at the latest version
            ansible.builtin.yum:
                name: httpd 
                state: latest
           - name: Write the apache config file 
              ansible.builtin.template: 
                   src: /srv/httpd.j2
                   dest: /etc/httpd.conf 
- name: Update db servers 
   hosts: databases remote_user: 
 …
…
```
- Roles are used to save and organize playbooks and allow sharing and reuse of playbooks.
```
- hosts: tomcat-node
 roles: 
      - {role: install-tomcat} #Looks in roles folder then in install-tomcat folder then uses main.yml
```
- Main folder structure example:
  - group_vars/
  - host_vars/
  - /roles
  - role_name/ (contains main.yml)
    - vars
    - tasks
    - tasks/
    - handlers/
- To create a role globally use ``ansible-galaxy init role_name``
  - Will create the following directory infrastructure in current working directory:
```
role_name/ 
    README.md 
    .travis.yml 
    defaults/ 
          main.yml 
    files/ 
    handlers/ 
           main.yml 
    meta/ 
           main.yml 
    templates/ 
    tests/ 
         inventory 
         test.yml 
    vars/ main.yml
```
- To launch Ansible playbooks, following components are needed:
  - Play: referenced in the actual playbook file
  - Task: referenced in the actual playbook file (within/under the play)
  - Inventory: referenced at the command line
  - Module: referenced at the command line
  - Role: referenced in the actual playbook file (optional)
- Behavior structure is the following:
  - Playbook: highest level and is a list of plays, needs inventory and credentials to run (use ``-i`` for inventory and ``-e`` for credentials)
    - Play: ties tasks to host lists (can have pre/post tasks and handlers and roles)
      - Tasks: definition of a call to a module
- Changes can be made and used in a config file which is searched in the following order:
  - ``ANSIBLE_CONFIG`` (environment variable if set)
  - ``ansible.cfg`` (in the current directory)
  - ``~/.ansible.cfg`` (in the home directory)
  - ``/etc/ansible/ansible.cfg``
- View configurations using the following commands:
  - ``ansible-config list`` (lists all configurations)
  - ``ansible-config view`` (shows the current config file)
  - ``ansible-config dump`` (shows the current settings)


**Add'l info**
https://docs.ansible.com/ansible/2.9/modules/list_of_all_modules.html