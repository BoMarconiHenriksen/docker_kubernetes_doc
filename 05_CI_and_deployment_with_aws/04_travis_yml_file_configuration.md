# Travis YML file Configuration
For this we are starting with the tests.
This is what we are going to tell Travis to do.  
1. Tell Travis we need a copy of docker running.  
2. Build our image using Dockerfile.dev.  
3. Tell Travis how to run our test suite.  
4. Tell Travis how to deploy our code to AWS(we are going to wait with this part).  
Lets get started!  
1. Create a Travis file in the root called ```.travis.yml```
2. Add this code to the .travis file.  
```
# We need super user permissions when using docker.
sudo: required
# Travis make sure docker cli is preinstalled.
services:
  - docker

# Before our test run make sure to do this.
before_install:
  - docker build -t bomarconi/docker-react -f Dockerfile.dev .

# The script section is going to contain all the commands to run the test suite.
script:
  # Make sure the test suite exit when it has been run with -- --coverage
  - docker run bomarconi/docker-react npm run test -- --coverage
```
To test if it works push the changes to github.  
Go to Travis webpage to check the test.  
