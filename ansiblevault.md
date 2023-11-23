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
- hosts: all // run in all the servers mentioned in the inventory
  gather_facts: false
  tasks:
    - name: vault_replace
      debug:
        msg: "{{ db_pass }}"

      Execute the command: ansible-playbook -e @password.yaml vault_playbook.yaml // -e help you to pass variables in one yaml to other yaml file

STEP 2: Encrypt the password file password.yaml
===============================================

ansible-vault encrypt password.yaml  // It will ask you to set a password

Now, do cat and check the content in the password.yaml.. You will see it is in encrypted format.

you can also, create your own encryption file for the very first time like this, 

**ansible-vault create password1.yaml**

**SOME USEFUL commands**

ansible-vault view password1.yaml

ansible-vault edit password1.yaml

ansible-vault decrypt password1.yaml

ansible-vault rekey password1.yaml

If you don't want to enter password during the command execution, then you can store the password in some key file and protect securely

ansible-vault view --vault-password-file key.txt password1.yaml // in this case, the password i have stored it in the key.txt


STEP 3: Apply secrets variable from password.yaml to playbook.yaml
==================================================================

ansible-playbook -e @password.yaml --ask-vault-pass vault_playbook.yaml
