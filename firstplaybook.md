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

**But you will have the ansible.cfg file already that comes as part of your installation**

but the new file will take the precedence

ansible all -m ping

Now it's time to create your first playbook
===========================================
vi firstplay.yaml

---

- hosts: all

  tasks:
  
    - name: install nginx
      
      debug:
      
        msg: Hello World
      

      **To run a playbook : ansible-playbook firstplay.yaml**

