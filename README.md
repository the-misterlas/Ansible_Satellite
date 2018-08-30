# ansible_home_lab
Ansible playbooks to build my home lab environment    
 usage:  
  - ansible-playbook -i inventory.txt build_lab.yml

# Key files:  
  inventory.txt - contains a list of hosts and groups them by function  
  /group_vars/all/vars/main.yml - variable file  
  /group_vars/all/vault/main.yml - vault file  
  /roles/satellite/files/satellite_manifest.zip  - manifest file downloaded from Red Hat  

# Downloading Manifest file:  
  Go to http://rhn.redhat.com.  
  Click "Subscription Allocations"  
  Select "New Subscription Allocation"  
  Enter name: "Satellite"  
  Select Type:  "6.3"  
  Click "Create"  
  Click "Subscriptions" and add the subscriptions and number of subscriptions to include in the manifest.  
  Select "Submit"   
  Click on "Export Manifest"  
  Name the file "satellite_manifest.zip" and download it to the /roles/satellite/files/ folder  
  
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
