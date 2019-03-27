# Applying Security Groups to Resources
1. Go to ElasticChache.  
2. Select Redis.  
3. Select the Redis instance and click modify.  
4. Click the VPC Security Group and select multi-docker(you now have 2 security groups selected).  
5. Save it.  
6. Go to the RDS dashboard and click databases.  
7. Select the multi-docker-postgres database and click modify.  
8. Scroll down to network & security and select multi-docker security group.  
9. Click continue and modify db instance.  
--- 
1. Go to Elastic Beanstalk.  
2. Click MultiDocker-env and then configuration.  
3. In the instances click modify.  
4. Scroll down to security groups and select multi-docker and apply.  
