Default inventory file
======================
cd /etc/ansible/

cat ansible.cfg

[default]

inventory=/etc/ansible/hosts  **// This is your inventory file**

Create your own Inventory
=============================================
[ansible@iam7hills firstplaybook]$ cat firstinventory

server1

server2

server3

ansible all --key-file /home/ansible/.ssh/ansible_control **-i firstinventory** -m ping

How to create your own ansible.cfg and store all your inventory and private key file
=====================================================================================
vi ansible.cfg

[defaults]
inventory = firstinventory
private_key_file = /home/ansible/.ssh/ansible_control
