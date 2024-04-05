### What is VSCode?
Lightweight source code editor. Visual Studio and Visual Studio Code are not the same thing. Visual Studio is an integrated development environment (IDE), and Visual Studio Code is a rich text editor. An integrated development environment (IDE) is a software application that provides comprehensive facilities for software development. An IDE normally consists of at least a source-code editor, build automation tools, and a debugger.
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/ea2eb843-264f-4167-8e98-86cc0d1d92a1)
You may need to download plugins or step out to run a code with a **code editor**.

### VSCode Capabilities
- Intellisense (suggestions and completion)
- Debugger
- Git Integration
- Extensions
- Terminal Integration

### Programming Language Support
- Python
- Ruby
- Go
- HTML
- C++
- CSS

## VSCode Setup
Set Terminal to `bash`. Check with `echo $0`. Bracket pair colorizer, Remote SSH extension.

## Connecting to a VM
### Configure VSCode
Hit `F1` search `>Remote-SSH: Connect to Host` click `Configure SSH Hosts...`, select the `\config` file and edit it to be:
```bash
Host Studx-VM
    HostName 172.16.x.x
    User studx
    IdentityFile ~/.ssh/id_rsa
```
### Copy SSH key to VM
```bash
ssh-copy-id -i <local_path_to_your_public_ssh_key> <your_student_#>@<IP_address_of_vm>
ssh-copy-id -i ~/.ssh/student_laptop.pub student1@172.16.x.x
```
### Connect in VSCode
Select `SSH Remote Explorer` and under SSH targets, select VM, and select the OS. Explore directories and such from here.

## Connecting to GitLab
Drop public SSH key into GitLab. `git clone` to your directory with link from GitLab and
```bash
git clone <SSH_clone_address_you_copied_in_step_1>
```
pen it in VSCode. Navigate to the directory with `cd` then open it with VSCode with the following command to reset the window.

```bash
code -r .
```

### Source Control
Open tab you see you can stage a file, discard, unstage, and commit. Remember to add a message in the box for a commit. You can push with the `sync` button. Or you can check the small circle in the bottom left. Check `git status` and `git log --oneline`.

### Branch Creation and Merging
Create a branch by selecting the `...` and Create Branch From... enter the name of the one you want. The Publish button pushes the branch to the remote repository. After committing the changes check on the `git log --oneline`. Change back to your `master` branch (or one you are merging into). Then select the `...` in source control again and `merge` option. Verify with the `git log --oneline`. Utilize the `sync changes` button to push it to the remote repository. 

### Resolving Conflicts
When you try to merge an editor comes up, so you can resolve the conflict.
```py
<<<<<<< HEAD
message = "Hello beautiful world!"
=======
message = "Hello blue world!"
>>>>>>> bug_fix
print(message)
```
Once the changes are made, add and commit the changes.

## Connect to Gitlab through a VM
Connect VM to VSCode. Create a new file in the `~/.ssh` folder called `config` and enter the following:
```bash
Host 10.10.44.20
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa
```
And give the file permissions to execute:
```bash
sudo chmod 700 config
```
Add the `id_rsa.pub` key to GitLab. Then copy the repo clone address
```bash
git clone git@10.10.44.20:Devops_1-24/Stud1_project.git
```
## Compare file creation methods
Just Paste stuff into VSCode its better for that.


![image](https://github.com/dpweldo/DEVOTC/assets/102386243/4bea0f52-8adc-4f6f-b360-14cfbc7198d4)

In the VSCode Remote explorer, this is also the config file to add to connect to a vm

```bash
Host Studx-vm
    HostName 172.16.x.x
    User studx
    IdentityFile ~/.ssh/studx_laptop
```
If you mess up the hostname on setup, change it with the following command

```bash
sudo hostnamectl set-hostname server1.example.com
cat /etc/hostname #confirm the change
```

