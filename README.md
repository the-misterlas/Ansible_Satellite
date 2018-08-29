# ansible_home_lab
Ansible playbooks to build my home lab environment    
 usage:  
  - ansible-playbook -i inventory.txt build_lab.yml

# Key files:  
  inventory.txt - contains a list of hosts and groups them by function  
  /group_vars/all/vars/main.yml - variable file  
  /group_vars/all/vault/main.yml - vault file  

# Roles:  
  satellite - Install Satellite 6.3.x   

# Minimum System Requirements for roles:  
  - satellite = RHEL7.4 with 20GB drive & 200GB drive (500GB recommended)  

# Vault Usage
A vault is used to manage admin passwords for this environment.  
The variables in use are:  
  #Satellite Variables  
-  vault_sat_admin_name: "<admin_name>"
-  vault_sat_admin_pwd: "<admin_password>"
