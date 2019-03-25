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

# How to Deploy/setup?

group_vars/all/users.yml file contains list of company super admins which should gain access to all created servers. Remove our example data and put list of your admins over there instead.

Create new folder inside environments for certain servers. For example these can be: production, testing or qa

Then create inventory file for the servers. This is an example:

[servers]
xxx.xxx.xxx.xxx
yyy.yyy.yyy.yyy
You can use hostnames or ip-addresses here.

Then add people involved with certain environments into:

environments/{{your-environment}}/group_vars/all/users.yml

ansible-playbook -i environments/production users.yml -u root --ask-pass

Note: You only need to do this once! On the next run you can run it like this:

ansible-playbook -i environments/production users.yml -u your-user-name-here

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




	     


