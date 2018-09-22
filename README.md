# Ansible_Satellite Playbook
Fork of https://github.com/calliey1/Ansible_Satellite_Day1

Steps to run:
  - Build RHEL 7.x (latest) host
  - Register with Red Hat Customer Portal
  - Attach Satellite entitlement
  - Add a disk of 200GB (or more/less, but be sure to adjust volume values in vars file)
  - Adjust roles/satellite/vars/main.yml to fit your needs and environment
  - Run playbook

Ansible playbooks to build my home lab environment    
 usage:  
  - ansible-playbook -i inventory satellite.yml -e "hostgroup=satellite" --ask-vault-pass

# Key files:  
  - inventory - contains a list of hosts and groups them by function  
  - roles/satellite/vars/main.yml - variable file  
  - roles/satellite/files/satellite_manifest.zip  - manifest file downloaded from Red Hat  

# Downloading Manifest file:  
  - Go to http://rhn.redhat.com.  
  - Click "Subscription Allocations"  
  - Select "New Subscription Allocation"  
  - Enter name: "Satellite"  
  - Select Type:  "6.3"  
  - Click "Create"  
  - Click "Subscriptions" and add the subscriptions and number of subscriptions to include in the manifest.  
  - Select "Submit"   
  - Click on "Export Manifest"  
  - Name the file "satellite_manifest.zip" and download it to the roles/satellite/files/ folder  
  
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

 Vaulted values are stored inline in roles/satellite/vars/main.yml.  To recreate:
  - ansible-vault encrypt_string Password123 --ask-vault-pass
