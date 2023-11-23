ANSIBLE STEP BY STEP PROCESS
============================

STEP 1: First create the password in a plaintext
=============================================

cat password.yaml

   --- // first line
   
   db_pass: "oracle-password" //password in plain text , which will be encrypted and substituted in the playbook.yaml

   **Sample playbook file and where we are substituting the password as a variable**

[ansible@iam7hills vault]$ cat vault_playbook.yaml
---
- hosts: all
  gather_facts: false
  tasks:
    - name: vault_replace
      debug:
        msg: "{{ db_pass }}"
