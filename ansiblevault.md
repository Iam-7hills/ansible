ANSIBLE STEP BY STEP PROCESS
============================

STEP 1: First create the password in a plaintext
=============================================

cat password.yaml

   --- // first line
   
   db_pass: "oracle-password" //password in plain text , which will be encrypted and substituted in the playbook.yaml
