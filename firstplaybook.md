Default inventory file
======================
cd /home/ansible/.ssh

ansible all --key-file ansible_control -m ping

**How to avoid giving --key-file in the CLI**
=============================================
First locate your inventory file, in my case

inventory path : /etc/ansible/ansible.cfg


export host_key_checking = False

or add a new line to cfg file
