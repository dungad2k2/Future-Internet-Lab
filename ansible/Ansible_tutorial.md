# Ansible Tutorial
## <b>1.Installation</b>:
Run step by step three commands below:
<!-- Code Blocks -->
``` BASH
~$ sudo apt update -y

~$ sudo apt-add-repository ppa:ansible/ansible

~$ sudo apt-add-repository ppa:ansible/ansible

```
## <b>2.Add authorized_keys to your server that you want manage</b>:
<b>Step 1: Create a key-gen </b>
<!-- Code Blocks -->
``` BASH
~$ ssh-keygen
```
<b>Step 2: Copy public key to your server</b>
<!-- Code Blocks -->
``` BASH
~$ ssh-copy-id -i id_rsa.pub your_server_name@your_server_ip
```
## <b>3. Inventory file:
* Type of parameters in inventory file:
  * <b>ansible_user</b>: this field is about username of host that ansible can use this name to ssh to host.
  *  