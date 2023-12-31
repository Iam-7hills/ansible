STEP 1 : Install Hashi vault
=============================
**Follow the below commands from Hashi vault tutorial:** https://developer.hashicorp.com/vault/install

Note : I am using Centos, so I have followed RHEL one,

a.  sudo yum install -y yum-utils

b.  sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo

c.  sudo yum -y install vault

**optional** : pip install hvac // for me i got an error while running playbook, so i had to install

STEP 2: Start Hashi Vault
=========================
vault server -dev -dev-listen-address="enter your ip:8200"

STEP 3: Create secrets in Hashi Vault
=====================================

export VAULT_ADDR='http://enter your ip:8200'

**To create a secret in HASHI VAULT**: vault kv put secret/password/vaultdemo data=itsasecret

**To retrieve a secret**: vault kv get -mount="secret" "password/vaultdemo"

**Note:** you can also create secrets from the browser


STEP 4: Write Ansible playbook
===============================

https://github.com/Iam-7hills/ansible/blob/main/ansibledemo/hashivault/hashivault.yaml

---
- hosts: server1
  
  vars:
  
    vault_token: 'enter your vault-token'
  
    vault_url: '<ip- need to enter>:8200'
  
    vault_pass: "{{lookup('hashi_vault', 'secret=secret/password/vaultdemo:data token={{ vault_token }} url={{ vault_url }}') }}"
  
  tasks:
  
  - name: Hashivault integration with Ansible
    
    debug:
    
      msg: "Retrieve password from Hashivault {{ vault_pass }}"

STEP 5: Run Playbook
====================

  ansible-playbook hashivault_playbook.yaml
    
    
