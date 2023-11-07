# ansible

**Step 1:
--------**
Install ansible

sudo yum install epel-release
sudo yum install ansible


Step 2:
========
	sudo vi /etc/hosts

	# Add the list of IP and host
	example:

	<ip> <hostname>
192.168.86.245 server1
192.168.86.246 server2
192.168.86.248 server3

step 3:
========

	cd /etc/ansible

	modify two files ; 

	1. hosts
	2. ansible.cfg

	vi /etc/ansible/hosts

	###   add below lines

server1
server2
server3

vi /ect/ansible/ansible.cfg:

	## add below lines

[default]
inventory=/etc/ansible/hosts

Step 4:
========

verify the ping pong

ansible all -m ping


step 5:
-------------

ssh-keygen -t ed25519 -C "Ansible"

ssh-copy-id -i ~/.ssh/ansible_control.pub server1
ssh-copy-id -i ~/.ssh/ansible_control.pub server2
ssh-copy-id -i ~/.ssh/ansible_control.pub server3


Step5:
-----

Test Connection

ansible all --key-file ansible_control -m ping
