STEP 1 : Install Hashivault
==========================
**Follow the below commands from Hashivault tutorial:** https://developer.hashicorp.com/vault/install

a.  sudo yum install -y yum-utils

b.  sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo

c.  sudo yum -y install vault

**optional** : pip install hvac // for me i got an error while running playbook, so i had to install

STEP 2: START HASHIVAULT
=======================
vault server -dev -dev-listen-address="<ip>:8200"
