Default inventory file
======================
cd /etc/ansible/

cat ansible.cfg
[default]
inventory=/etc/ansible/hosts  // This is your inventory file
host_key_checking = False

Create your own Inventory
=============================================
[ansible@iam7hills firstplaybook]$ cat firstinventory
server1

server2

server3

ansible all --key-file /home/ansible/.ssh/ansible_control -i firstinventory -m ping
