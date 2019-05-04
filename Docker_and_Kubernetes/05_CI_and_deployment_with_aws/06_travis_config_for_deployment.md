# Travis Config for Deployment
1. Go to your .travis.yml file.  
2. Add this code.  
```
# For deployment on aws
deploy:
  # Travis has implemented diffrent providers. For region see the url in beanstalk.
  provider: elasticbeanstalk
  region: us-east-2
  app: "docker"
  env: "Docker-env"
  # hd on aws. Click services, enter s3, click the link and get the name.
  bucket_name: "elasticbeanstalk-us-east-2-338074124185"
  bucket_path: "docker"
  # Only deploy if pull request to master.
  on:
    branch: master
```
> We still need 2 more things before it's ready.  
### Generate API Keys
1. In aws click services and search for iam(manage outside keys).  
2. Click users and then add user.  
3. Enter user name: docker-react-travis-ci  
4. Give Programmatic access only.  
5. Click Next: Permissions.  
6. Click Attach existing policies directly.  
7. Search for beanstalk and check provide full access to aws beanstalk and click Next: Tags.  
8. Click next: review and then create user.  
9. Be sure to save the secret access key. It's only showen here.  
10. Go to Travis dashboard.  
11. Go to more options and click settings.  
12. Scroll down to enviroment variables.  
13. Name: AWS_ACCESS_KEY Value: copy/paste the key from aws. Then click add.  
14. Name: AWS_SECRET_KEY Value: copy/paste the secret key from aws. Then click add.  
15. Go to .travis.yml file.  
16. Add this code to the file.  
```
access_key_id: $AWS_ACCESS_KEY
  secret_access_key:
    secure: "$AWS_SECRET_KEY"
```
17. Push to master to check that it's working.  
It wont because we need to expose ports...  
