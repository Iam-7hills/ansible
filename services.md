How to run Linux Services using Ansible playbook
================================================

Create your inventory and ansible.cfg as a pre-requisite.

Sample yaml 
===========

---
- hosts: all
  become: yes
  tasks:
    - name: To install nginx
      yum:
        name: nginx
        state: latest

    - name: To start nginx
      service:
        name: nginx
        state: started

    - name: To stop nginx
      service:
        name: nginx
        state: stopped

    - name: To install nginx
      yum:
        name: nginx
        state: absent

  How to run a playbook
  =====================
  ansible-playbook --ask-become-pass becomeuser.yaml
