# Ansible_Satellite Playbook
Fork of https://github.com/calliey1/Ansible_Satellite_Day1

Steps to run:
  - Build RHEL 7.x (latest) host
  - Register with Red Hat Customer Portal
  - Attach Satellite entitlement
  - Add a disk of 200GB (or more/less, but be sure to adjust volume values in vars file)
  - Run playbook

Ansible playbooks to build my home lab environment    
 usage:  
  - ansible-playbook -i inventory satellite.yml --ask-vault-pass

# Key files:  
  inventory - contains a list of hosts and groups them by function  
  roles/satellite/vars/main.yml - variable file  
  roles/satellite/files/satellite_manifest.zip  - manifest file downloaded from Red Hat  

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
  Name the file "satellite_manifest.zip" and download it to the roles/satellite/files/ folder  
  
# Roles:  
  satellite - Install Satellite 6.3.x   

# Minimum System Requirements for roles:  
 - satellite
  - RHEL7.x (latest)
  - 30GB  OS drive [sda]
  - 200GB content drive (500GB recommended) [sdb]
  - 4 CPU
  - 20GB memory

# Vault Usage
A vault is used to manage admin passwords for this environment.  

 To recreate the vault file:
  - rm ansible-vault create group_vars/all/vault/vault.yml
  - ansible-vault create group_vars/all/vault/vault.yml

The variables in use in the vault are: 

 # Satellite Variables:
  - vault_sat_admin_name: "admin_name"
  - vault_sat_admin_pwd: "admin_password"
