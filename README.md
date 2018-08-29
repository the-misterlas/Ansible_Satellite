# ansible_home_lab
Ansible playbooks to build my home lab environment    
 usage:  
  - ansible-playbook -i inventory.txt build_lab.yml

# Key files:  
  inventory.txt - contains a list of hosts and groups them by function  
  build_lab.yml - kickoff playbook    
  /vars/main.yml - vault file  

# Roles:  
  common - used to setup all hosts / register with RHN  
  ipa - Install and configure IdM  
  satellite - Install and configure Satellite 6.3.1   

# Minimum System Requirements for roles:  
  - common = RHEL7.x with 20GB drive  
  - ipa  = RHEL7.4 with 20GB drive  
  - satellite = RHEL7.4 with 20GB drive & 200GB drive (500GB recommended)  

# Vault Usage
A vault is used to manage admin passwords for this environment.  
The variables in use are:  

  #RHN Variables  
-  vault_rhn_user: "<RHN_user>"
-  vault_rhn_pwd: "<rhn_password>"

  #IPA Variables  
-  vault_ipa_admin_pwd: "<admin_password>"

  #Satellite Variables  
-  vault_sat_admin_name: "<admin_name>"
-  vault_sat_admin_pwd: "<admin_password>"
