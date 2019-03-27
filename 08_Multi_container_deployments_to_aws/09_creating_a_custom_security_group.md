# Creating a Custom Security Group
1. Go to the VPC's dashboard.  
2. On the left handside click security groups.  
3. Click create security group and enter:  
Name Tag: multi-docker
Description: Traffic for services in multi-docker app  
4. Select the default vpc and click create.  
5. Select the security group you just created in the vpc dashboard.  
6. Click inbound rules and edit.  
Port Range: 5432-6379  
Source(allow trafic from any other instance in the same security group): Enter the id of the security group you just created.  
7. Click save.  
