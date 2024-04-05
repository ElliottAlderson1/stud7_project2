## SSH Protocol
Secure shell remote login with strong encryption. Connects **SSH client with an SSH server**. Used to access shell accounts on remote servers. Replacement for old unsucured remote connections like `rlogin`, `rsh`, `Telnet`.

Uses the **client-server** architecture for secure communication over the network. Listens on TCP port 22. Uses public key cryptography technique, uses strong symmetric encryption & hashing algorithms.

Can use it for:
- login shell on remote host
- executing a single command on remote host
- setting up automatic login to remote server (OpenSSH)
- Combination with rsync to backup, copy, mirror files
- forwarding a port
- tunneling (not equal to VPN)
- file transfer mechanisms
- secure copy
- rsync more efficient than SCP
- SSH File Transfer Protocol
- FISH - file transfer over secure protocol
- FASP - fast and secure protocol (uses ssh for control, UDP for transfer)

#### SSH Supported Algorithms
- ECDSA, RSA, DSA for public key crypto
- ECDH and Diffie Hellman for key exchange
- HMAC, AEAD, and UMAC for MAC
- AES for symmetric encruption
- AES-GCM 
- SHA for key fingerprint

## SSH Commands
- `sshd` initiates the SSH server, enables authorized systems to connect to the local host
- `ssh-keygen` creates a new authentication key pair for SSH
- `ssh-copy-id` copy, install and configure an SSH key on a server to automate password-less logins and SSO
- `ssh-agent` tracks identity keys and their passphrases and  identity keys to log in to different servers without the need to reenter passwords or passphrases
- `ssh-add` add a key to the SSH authentication agent and is used with ssh-agent to implement SSO using SSH.
- `scp` copying files from one computer to another and is an SSH-secured version of rcp.
- `sftp` copy files from one computer to another and is an SSH-secured version of ft. preferred, replacing both FTP and FTP/S (FTP Secure), which is a protocol for using FTP over an SSL/TLS tunnel.

## SSH key generation
~~~bash
ssh-keygen 
~~~
Choosing an Algorithm and Key Size
~~~bash
ssh-keygen –t (rsa -b 2048)
ssh-keygen -t rsa -b 2048
rsa 2048/4096
ecdsa 256/384/521
~~~
Specify the File Name. This will mainly be stored with the default id_rsa. Each key can be given a separate name based on use. Then it will ask you for a passphrase.

## Adding it to GitLab
Display the contents of the public key `~/.ssh/id_rsa.pub`
~~~bash
cat ~/.ssh/id_rsa.pub
~~~
`ctrl +c` to copy, paste into GitLab `profile settings` - `preferences` - `SSH keys`, then paste contents of the public key file, leave expiration blank. Add key.

## Connecting to Remote Repo
Log into GitLab click on copy icon for `git@....` address for the ssh key. From the local repository, add remote repository
~~~bash
git remote add origin <SSH_clone_address>
~~~
Verify the settings of Git remote
~~~bash
git remote -v
~~~

### Creating a local clone

Copy SSH address from Project in GitLab. Then create the local clone:

~~~bash
git clone <SSH_clone_address_you_copied>
~~~
Verify the remote.
~~~bash
git remote -v
~~~

Should display the origin location
~~~bash 
origin  git@bitbucket.com:origin_user/reponame.git (fetch)
origin  git@bitbucket.com:origin_user/reponame.git (push)
~~~

From the new branch push the local 'main' to remote
~~~bash
git push -u origin main
~~~

The -u [--set-upstream] indicates that for every branch that is up to date or successfully pushed, add upstream (tracking) reference, used by argument-less git-pull[1] and other commands.

Verify remotes, use the `-r` option
~~~bash
git remote -r
~~~

Verify by checking GitLab


### Adding a Remote Lab Notes
Always `push` then `pull` before starting work. `Fetch` does both of them. Change into branch with the `checkout`.

Show the repositories you are already connected to
~~~bash
git remote
~~~
Add a remote:
~~~bash
git remote add origin <SSH_clone_address_you_copied_in_step_1>
~~~
Display the current git remote:
~~~bash
git remote -v
~~~
 Push the local git master to remote GitLab Repo with
~~~bash
git push -u origin master
~~~
View remote branches from local repo using
~~~bash
git branch -r
~~~

Override name of initial branch
~~~bash
git init -b <name>
~~~

## Performing Version Control and Branch Command
Create a new branch. This creates a new pointer.
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/6bf01e2b-1b88-4e0f-896a-c482b1567eda)
Create a branch
~~~bash 
git branch [new-branch-name]
git switch - c [new-branch-name]
~~~
This creates new branch in same state as original branch. You can rename it with:
~~~bash
git branch -m old-name new-name
~~~

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/6009db83-4317-4ea4-afd4-f08343590405)

#### Switching Branches
~~~bash
git branch [new-branch-name]
git switch [new-branch-name]
~~~

HEAD Points to the current branch.
~~~

## Remote Git Lab Notes
~~~bash
git branch # local repo branches list
git branch -r # remote list
~~~

Create a new branch
~~~bash
git branch <new-branch> #creates it
git push origin my_new_branch #creates it on the remote repo, it is not being tracked, so you need to specify it on push pull
git branch -u origin/my_new_branch my_new_branch #sets the new branch to be tracked
cat .git/config #where you can check for it
git branch --unset-upstream my_new_branch #untrack the new branch
git branch -d my_new_branch #delete the branch
~~~
You can create a new branch off another branch (off master here)
~~~bash
git branch my_other_branch master
~~~
Set up tracking automatically
~~~bash
git push -u origin my_other_branch
~~~

## Collaborate using remote Git Repo Notes

To see the SHA of a commit
~~~bash
git log --oneline
~~~
Push local master to origin/master
~~~bash
git push
~~~
Look at 3 commans in specific liocal copy of origin/master branch. See where the HEAD pointer commit is. It is the most recent commit in the branch.
~~~bash
git log --oneline origin/master -3
~~~

Always fetch before a merge. 

`push` will update local, showing sally's changes in bill's updated logs repo.

#### Checking out a branch
Create a new branch
~~~bash
git checkout -b bill_code_changes master
~~~

Push changes of branch `bill_code_changes` to remote
~~~bash
git push -u origin bill_code_changes
~~~

Switch to master branch and delete the branch with one of the following
~~~bash
git push origin :bill_code_changes
git push origin --delete bill_code_changes
~~~

If you try to merge with that deleted branch still in there it will mistake, so you must Delete locally with 
~~~bash
git branch -d bill_code_changes
~~~
You can force delete with `-D` instead of `-d`

If the master branch is your current checkout you merge `origin/master` into it with:
~~~bash
git merge origin/master
~~~

Remove any deleted remote branches that exist locally with this fetch
~~~bash
git fetch --prune
~~~

![nWYnQ](https://github.com/dpweldo/DEVOTC/assets/102386243/a4675054-f4f2-4da4-af81-d926ce5122c3)
