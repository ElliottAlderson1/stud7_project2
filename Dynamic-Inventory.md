**Procedures/Commands**

- .YML File (can target specific groups by changing ``hosts`` value):
```yaml
---
- name: Debug Inventory
  hosts: all
  gather_facts: false
  connection: local

  tasks:
    - name: Debug Variables
      debug:
        var: domain_name
```
- inventory.py file:
```python
#!/usr/bin/env python3

#import necessary modules
import requests
import urllib3
import json

#Disable warnings due to SSL certs
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

#Define API token and URL
NAUTOBOT_TOKEN = '4708ad7c80f2734f85a4b3e1d4ca5d18223cab08'
DEVICES_URL = 'https://10.10.44.21/api/dcim/devices'

#Define required HTTP headers
HEADERS = {
        'Application': 'application/json',
        'Content-Type': 'application/json',
        'Authorization': f'Token {NAUTOBOT_TOKEN}'
}

#Define query filters
PARAMETERS = {
        'site': 'lab19'
}

#Execute API call
devices = requests.get(url=DEVICES_URL, params=PARAMETERS, headers=HEADERS, verify=False).json()

#Create empty hostvars section
hostvars = {
        '_meta': {
                'hostvars': {}
        }
}

#Loop through each device in the API call results
for device in devices['results']:
        #Add a key to the hostvars dictionary that is the device's name
        hostvars['_meta']['hostvars'].update(
                {
                        device['name']: {
                                #Set the ansible_host to the primary IPv4 address of the device
                                'ansible_host': device['primary_ip4']['address'].split('/')[0],
                                #Set the device_type of each device
                                'device_type': device['device_type']['model']
                        }
                }
        )

#Create an empty inventory dictionary
inventory = {}

#Combine inventory dictionary with the hostvars
inventory.update(hostvars)

#Create group structure
groups = {
        'orko': {
                'children': [
                        'red_devices',
                        'yellow_devices'
                ]
        },
        'red_devices': {
                'hosts': [],
                'vars': {
                        'domain_name': 'red.local'
                }
        },
        'yellow_devices': {
                'hosts': [],
                'vars': {
                        'domain_name': 'yellow.local'
                }
        }
}

#Add each red device to the red_devices group
for device in devices['results']:
        if device['platform']['name'] == 'red':
                groups['red_devices']['hosts'].append(device['name'])

#Add each yellow device to the yellow_devices group
for device in devices['results']:
        if device['platform']['name'] == 'yellow':
                groups['yellow_devices']['hosts'].append(device['name'])

#Add the groups to the master inventory variable
inventory.update(groups)

#Print out json-formatted string
print(json.dumps(inventory, indent=4))
```
