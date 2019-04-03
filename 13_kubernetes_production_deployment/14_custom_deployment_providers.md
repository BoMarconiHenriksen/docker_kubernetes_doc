# Custom Deployment Providers
If the tests was succesful we want to deploy.  
For this we are going to write a script thats going to build our images, tag them, push them to docker hub, apply all the config files and set the imperativ command for latest image for each deployment.  
#### Why is it in a seperate file?
Travis does not have a provider for Kubernetes so we have to make our own script.  

In the .travis.yml file create a deploy section and add this code.  
```
deploy:
  provider: script
  # The command to run the script
  script: bash ./deploy.sh
  on:
    branch: master
```
##### Inside the root folder of the project create a file called deploy.sh
