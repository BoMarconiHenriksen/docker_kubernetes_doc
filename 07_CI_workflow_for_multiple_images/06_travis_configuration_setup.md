# Travis Configuration Setup
This is the flow for the travis file.  
1. Specify docker as a dependency.  
2. Build test version of React project(it's possible to add other test suites here).  
3. Run tests.  
4. Build production versions of all projects.
5. Push all to docker hub.  
6. Tell Elastic Beanstalk to update.  
---
1. In the root of the project create a file called ```.travis.yml```
2. Add this code to the file you just created.  
```
sudo: required
services:
  # We want to get access to a copy of docker
  - docker

Before_install:
  # Build a test version of our client project
  # We use the Dockerfile.dev because we only get access to the test suites when we have all other dependencies attached to the project
  # We can not run test with the production file. -t = tag and -f = specify a dockerfile in the client folder and ./client is the build context
  - docker build -t bomarconi/react-test -f ./client/Dockerfile.dev ./client
  # - docker build myOtherProject...

# If a test fail the scipt will exit with a number higer than 0
script:
  # To get out of watch mode after npm test run use -- --coverage
  - docker run bomarconi/react-test npm test -- --coverage
  # - docker run myOtherProject runMyTests

# Build production versions of all our projects and then to docker hub
after_success:
  - docker build -t bomarconi/multi-client ./client
  - docker build -t bomarconi/multi-nginx ./nginx
  - docker build -t bomarconi/multi-server ./server
  - docker build -t bomarconi/multi-worker ./worker
```
We still need to add the push to docker hub. See next section.  
