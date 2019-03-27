# Overview of AWS VPC's and Security Groups
We want to connect our containers in the elastic beanstalk instance with RDS and EC.  
By default these services can't talk to eachother.  
We have to form up links between the 2 with some clicks...  
In your region you got created an VPC(Virtual Privat Cloud). It's a privat little network so that any instance/service you create is isolated to just your account.  
It also create some security rules.  
You get one default VPC per region.  
You can search for vpc and get an overview of your vpc.  
### Get the diffrent services to connect to eachother
We have to create a security group(firewall rules).  
As an example this is what you can do.
1. Allow any incomming traffic on port 80 from any IP.  
2. Allow traffic on Port 3010 from IP 172.0.40.2  
---
1. Go to your VPC dashboard and in the left column click security groups.  
2. What we want to do:  
*Allow any traffic from any other AWS service that has this security group.*  
So we are going to create a security group and attach it to alle 3 instances(EB instance, RDS and EC).  
