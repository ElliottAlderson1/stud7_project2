### Install git
```bash
sudo yum install git -y
```

### Install the `httpd` package
```bash
sudo yum install httpd
yum list installed | grep httpd
```
### Enable httpd service
Check the status with
```bash
sudo systemctl status httpd
```
Activate `httpd` service 
```bash
sudo systemctl start httpd
```
```bash
sudo systemctl enable httpd
```
### Actually Create the webpage
Change to /var directory and change the group ownership of /var/www/ recursivly
```bash
cd /var
sudo chown -R <studx>:<studx> www
``` 
The `-R` is for recursive the `<studx>:<studx>` is for `<user>:<group>` and `www` is the directory

Next remove the html directory from /var/www/ before cloning from git.
```bash
rm -rf html
```


## Cloning a Apache HTML repo from GitLab
After creating the repository on GitLab, remember to add your ssh key to GitLab on the VM, and then configure your ID. Instructions are automatically given by GitLab.
```bash
git config --global user.name "studx"
git config --global user.email "studx@local.com"
git clone <ssh link>
```
### Creating the index.html
```bash
vim index.html
```
Then write your html script.
### Disable Firewalls
It will not show up until you disable the http firewall on TCP port 80.
```bash
sudo firewall-cmd --add-port=80/tcp --permanent
sudo firewall-cmd --reload
```
The site should show up.

## Version Control With Git and VSCode
Connect to VSCode. Hit `F1` search `>Remote-SSH: Connect to Host` click `Configure SSH Hosts...`, select the `\config` file and edit it to be:
```bash
Host Studx-VM
    HostName 172.16.x.x
    User studx
    IdentityFile ~/.ssh/id_rsa
```
You can modify code and version control from here with the tutorial [[on Version Control with VSCode |VSCode]]

```bash
git remote -v
```