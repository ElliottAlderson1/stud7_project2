## Connecting VS Code to VM
- Generate SSH key on laptop
- Configure VS Code Remote Explorer
  - Open VS Code
  - Press ```F1```
  - Enter ```Remote-SSH: Connect to Host```
  - Select ```Configure SSH Host```
  - Select option that ends with \config
  - Add the following:
```bash
Host <name of vm>
   HostName <ip address>
   User <username of vm>
   IdentityFile <path to private ssh key>
```
- Copy public ssh key to vm
  - Use ```ssh-copy-id -i <path to public key> <vm username>@<vm ip address>```

## Connect to GitLab from a VM through VS Code
- Open home folder of vm
  - From VS Code connect to vm
- Open a terminal
- Generate a SSH Key
- Setup SSH config file on VM
  - Create a new file named config in the ```.ssh``` folder
  - Add the following:
```bash
Host <IP of GitLab server>
   PreferredAuthentications publickey
   IdentityFile <path to private key>
```
  - Change permissions on the config file
     - ```chmod 700 config```
- Configure SSH Authentication on GitLab
  - Open public key in VS Code and copy it
  - Add public key to GitLab
     - Go to user preferences
     - Go to SSH Keys
     - Add the VM's public key

