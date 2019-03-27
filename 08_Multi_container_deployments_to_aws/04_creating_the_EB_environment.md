# Creating the EB Environment
We have to make an environment on Elastic Beanstalk that going to serve as the target that we are going to deploy to.  
1. Login to your AWS account.  
2. Go to Elastic Beanstalk.  
3. Click create new application. Name: multi-docker  
4. Click on create one now (creating an environment).  
5. Select webserver environment.  
6. Go to base configuration and in platform select multi-container docker and then click create environment.  
---
### Databases in containers
One thing we haven not look at is the postgres database and redis.  
See next section.  
