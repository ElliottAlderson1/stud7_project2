## Key Generation
```bash
ssh-keygen -t rsa -b 2048
```
Name it if you will have multiple on the machine. `cat` out the key and `.pub` file to retrieve it.
### How to Copy to VM
```bash
ssh-copy-id -i <file_path_to_your_public_ssh_key> <your_student_#>@<IP_address_of_vm>
ssh-copy-id -i ~/.ssh/stud10_laptop.pub student1@172.16.10.25
```
### SSH with the private key

```bash
ssh <student_username_on_vm>@<ip_address_of_vm> -i <local_path_to_your_private_ssh_key_created_above>
ssh studx@172.16.10.25 -i ~/.ssh/studx_Laptop
```
You should not have to enter password