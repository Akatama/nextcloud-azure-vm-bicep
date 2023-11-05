## nextcloud-azure-vm-bicep
Automating the process of creating a Nextcloud instance on an Azure VM

This project is broken into multiple parts

### part_1_base
This part has all the files necessary to install nextcloud on an Ubuntu server, with the assumption that we will use Azure DevOps. This includes database itself, so this wouldn't be very good if you need high availability or disaster recovery options. However, as I am using this project to learn, it was a very good opportunity for me to learn about configuration management.

If you don't want to use a pipeline to deploy this, using the provided genKeyAndCallBicep.ps1 PowerShell script (or manually doing the same steps as shown in the PowerShell script) with the Ansible files will succeed in installing Nextcloud and properly setting up everything.

Included here:
* A Bicep file to deploy the VM, which includes an NSG and public IP. Currently this bicep file connects to an already existing VNet
* A PowerShell script which generates a new SSH Key, then takes all the parameters and calls the Bicep file.
* An Ansible Playbook
* An Ansible Vault encypted password file, which contains the password for both the database admin and the first user of Nextcloud
* An Ansible Configuration file, along with a static.ini for inventory
* A few files that the Ansible Playbook needs, such as the nextcloud.conf and config.php.j2

### part_2_remote_db
The purpose of this part is to do the same thing as part_1_base, but have a remote database. This part will be mostly getting us set up for future parts

### part_3_high_availability
Coming soon

### part_4_disaster_recovery
Coming soon