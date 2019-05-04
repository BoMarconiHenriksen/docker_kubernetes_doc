# IAM Keys for Deployment
We want to tell AWS that there are new images.  
We have to send the Dockerrun.aws.json file to AWS. When Elastic Beanstalk get the file it will pull the images from docker hub. But first we'll create a AWS user and set the id and secret in a environment variable in travis.  
---
1. AWS search for IAM and go to the users section(we are going to create a new user with deploy access to Elastic Beanstalk).  
2. Click add user and give it the user name: multi-docker-deployer and then select programatic access and then next: permissions.  
3. Click attach existing policies directly and search for beanstal.  
4. Select all withAWSElasticBeanstalk(This can be more fine grained in a real app) and click next: review(skip tags) and then create user.  
5. Go to travis-ci.org  
6. Go to multi-docker project, more options and then select ssettings.  
7. Setup access to AWS.  
```Name: AWS_ACCESS_KEY - Value: <aws access key id for user>``` and click add.  
```Name: AWS_SECRET_KEY - Value: <aws secret access key for user>``` and click add.  
