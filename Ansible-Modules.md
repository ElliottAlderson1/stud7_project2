**Procedures/Commands**

- Use Fully Qualified Collection Names to ensure the correct module is being called upon.
- File Module parameters:
  - ``owner`` is the user who'll own the created file/directory
  - ``path`` is path to file or directory to manage
  - ``mode`` is to set permissions (such as ``0777`` or ``0644``)
  - ``group`` sets the group ownership
  - ``force`` is a boolean value used to create symlinks if source file is not currently available
  - ``follow`` tracks filesystem if it exists
  - ``attributes`` sets attributes to file or directory
  - ``state`` defines context:
    - ``touch`` creates an empty file
    - ``directory`` creates an empty directory
    - ``hard`` creates a hard link
    - ``link`` creates a soft link
    - ``absent`` delete files and directory recursively and unlink links
  - ``access_time`` sets file's access Default is "preserve" means no modification needed
  - ``access_time format`` sets time format, default format is ``“%Y%m%d%H%M.%S”``
  - ``modification_time`` sets file modification time Default is "preserve" and no modification needed
  - ``modification_time_format`` sets time format of modification time, default is ``“%Y%m%d%H%M.%S”``
  - ``recurse`` updates content of a directory in terms of file attributes
  - ``selevel``, ``serole``, ``setype``, ``seuser`` updates selinux file context
  - ``src``: give the path of a file to link to
```yaml
- name: CREATE A DIRECTORY IF IT DOES NOT EXIST
  ansible.builtin.file:
    path: "~/playbook"
    state: directory
    mode: '0755'

- name: CHANGE FILE OWNERSHIP, GROUP AND PERMISSIONS
  ansible.builtin.file:
    path: "~/playbook/inventory.py"
    owner: root
    group: root
    mode: '0644'
```
- To create a file and add content into use the following structure:
```yaml
---
hosts: all
  tasks:
    name: Create a file with content
    copy:
      dest: "/your path"
      content: |
        line 01
        line 02
```
- Create multiple files using a single task:
```yaml
hosts: all
  tasks:
    name: Create multiple files
    file:
      path: "{{ item }}"
      state: touch
    with_items:
    - test01.txt
    - test02.txt
    - test03.txt
    - test04.txt
```

![module_parameters](uploads/3edfbd2143639c48ebf5c69fecfb891a/module_parameters.png)

- If using ``scp`` on network device with paramiko, use ``protocol=scp``
- Use the ``uri`` module for cases like checking status of webpages and validating status codes, ex:
```yaml
- name: Check that a page returns a status of 200
  uri:
    url: http://www.example.com
    return_content: yes
  register: this
  failed_when: '"AWESOME" not in this.content'
```
- Can also call an API using the ``uri`` module using ``GET``:
```yaml
---
- name: Example API call in ansible
  uri:
    url: https://demo.nautobot.com/api/dcim/device
    method: GET
```
-  Storing device configuration example:
```yaml
---
- name: set current time
    set_fact:
      start_time: "{{ lookup('pipe', 'date + %Y%m%d%H%M%S') }}"
    delegate_to: localhost

- name: create a directory for config files
    file:
      path: "{{ playbook_dir }}/{{ start_time }}-configs"
      state: directory
    delegate_to: localhost

- name: generate device config files
    template:
      src: base.j2
      dest: "{{ playbook_dir }}/{{ start_time }}-configs/{{ inventory_hostname }}.cfg"
    ignore_errors: true

- name: send configs
    ios_config:
      src: base.j2
```
**COMPREHENSIVE FILE MODULE PLAYBOOK**
```yaml
---
- name: USING THE FILE MODULE
  hosts: localhost
  connection: local
  gather_facts: false
  
  tasks:
    - name: PRINT TASK MESSAGE
      debug:
        msg: "The playbook is starting..."

    - name: CREATE A DIRECTORY
      file:
        path: "{{ playbook_dir }}/my_new_directory/"
        state: directory

    - name: CREATE A FILE
      file:
        path: "{{ playbook_dir }}/my_new_directory/file_1.cfg"
        mode: '0744'
        state: touch

    - name: CHANGE FILE PERMISSIONS
      file:
        path: "{{ playbook_dir }}/my_new_directory/file_1.cfg"
        mode: a+x

    - name: GIVE DIRECTORY INSECURE PERMISSIONS
      file:
        path: "{{ playbook_dir }}/my_new_directory"
        state: directory
        recurse: true
        mode: '0777'

    - name: CHANGE OWNER AND GROUP TO ROOT
      file:
        path: "{{ playbook_dir }}/my_new_directory/file_1.cfg"
        owner: root
        group: root
      become: true

    - name: DELETE THE FILE #HAVE TO RM -RF THE DIRECTORY OTHERWISE CREATE A FILE TASK WILL FAIL
      file:
        path: "{{ playbook_dir }}/my_new_directory/file_1.cfg"
        state: absent
      become: true

    - name: DELETE THE DIRECTORY
      file:
        path: "{{ playbook_dir }}/my_new_directory"
        state: absent
```