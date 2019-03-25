# Ansible-users
Automate the process of granting / revoking SSH access to a group of servers instances to a new developer.

# Description:

Automate the process of granting / revoking SSH access to a group of servers instances to a new developer using ansible


# Prerequisites:
Ansible installed on the machine.

# Steps to follow:

Step1: create a folder/project/repo (in git) where you will manage all users and initialize git
Example: mkdir Ansible0users


Step2: Create yml ansible file for the user config which includes creating groups and user granting/removal (say Axelerant-users.yml)


Step3: add servers in inventory section


Step4: (optional if you have already installed) install ansible


step5: deploy user using ansible command


ansible-playbook -i inventory Axelerant-users.yml -u root --ask-pass



Step6: verify by logging using that particular user which you have created


Step7: update all your changes to git



# Alternate method:

Automate the process of granting / revoking SSH access to a group of servers instances to a new developer using chef

# Prerequisites:

Befoe creating/removing user, we have to install chef in our stack . Process is quite simple--

Step1: create instances (say workstation instance and node instances)

Step2: Create chef account under manage.chef.io

Step3: Download the starter kit 

Step4: Now, Connect to your workstation ec2 instance and then install chef dk software on it.

Step5: Also copy the download starter kit (from step3) to your workstation ec2 instance

Step6: As a output, chef-repo directory will be created 

Step7: Now, connect to you node ec2 instance (ypu will see that nothing related to chef is installed in it)

Step 8: Now go into your workstance instance and run one bootstap command under chef-repo directory to add node. command will 
be like ->

knife bootstrap node_instance_ip --ssh-user ec2-user --sudo --identity-file "pem file" -N "node name" 

NOTE: make sure you have pem file under folder chef-repo in your workstation ec2 instance

After completing above steps, we can simple manage users by creating receipes




	     


