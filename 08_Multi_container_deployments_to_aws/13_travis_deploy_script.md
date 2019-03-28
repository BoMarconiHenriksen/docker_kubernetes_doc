# Travis Deploy Script
1. Go to the .travis.yml file and make a deploy section.  
2. Add the following code.  
```
deploy:
  provider: elsaticBeanstalk
  region: us-east-2
  app: multi-docker
  env: MultiDocker-env
  bucket_name: elasticbeanstalk-us-east-2-338074124185
  bucket_path: docker-multi
  on:
    branch: master
  access_key_id: $AWS_ACCESS_KEY
  secret_access_id:
    secure: $AWS_SECRET_KEY
```
*bucket_name and bucket_path* is where travis zips up our project and stach it inside a s3 bucket.  
1. Check that we have an s3 bucket. So search s3 and click on the previous created bucket.  
2. Copy the bucket name.  
```
on:
    branch: master
```
Deploy only when code checge on master branch.  
> Push your code to gethub and check that travis build all the images.  
