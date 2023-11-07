ANSIBLE Installation and creating the inventory file
======================================================

Pre-requisite:
==============
	Create user id and make sure that ssh is working from control plane 
 	example from control plane : ssh <managed-node>

Step 1 - Install Ansible:
=========================
	sudo yum install epel-release
	sudo yum install ansible

Step 2 - Modify /etc/hosts:
===========================
	sudo vi /etc/hosts

	# Add the list of IP and host
	example:

	<ip> <hostname>
	192.168.86.245 server1
	192.168.86.246 server2
	192.168.86.248 server3

step 3 - hosts and ansible.cfg under ansible installed folder:
============================================================

	cd /etc/ansible

	modify two files ; 

	1. hosts
	2. ansible.cfg

	sudo vi /etc/ansible/hosts

	###   add below lines

	server1
	server2
	server3

	sudo vi /etc/ansible/ansible.cfg:

	## add below lines

	[default]
	inventory=/etc/ansible/hosts

Step 4 - Precheck ansible - This step will throw error and expected:
====================================================================

	verify the ping pong

	ansible all -m ping


step 5 - Generate Keygen and copy the pub file in all the targeted servers:
==========================================================================

	ssh-keygen -t ed25519 -C "Ansible"

	path to provide : /home/ansible/.ssh/ansible_control

	ssh-copy-id -i ~/.ssh/ansible_control.pub server1
	ssh-copy-id -i ~/.ssh/ansible_control.pub server2
	ssh-copy-id -i ~/.ssh/ansible_control.pub server3

 	Validate - if you can do ssh without asking password

  	ssh -i ~/.ssh/ansible_control server1
   	ssh -i ~/.ssh/ansible_control server2
    	ssh -i ~/.ssh/ansible_control server3


Step5 - Verify test connection
===============================

	Test Connection - By running ansible command

	ansible all --key-file ansible_control -m ping
