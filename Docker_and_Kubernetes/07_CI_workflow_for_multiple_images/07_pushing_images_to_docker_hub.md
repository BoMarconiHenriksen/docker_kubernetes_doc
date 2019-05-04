# Pushing Images to Docker Hub
1. Log in to the docker cli in .travis.yml file.  
2. We will also create an env file to hold credentials.  
--- 
1. On the travis homepage go to the multi-docker page and click more options and find settings.  
2. Find the environment section.  
3. Enter ```DOCKER_ID and value is <dockerId>``` and click add.  
4. Enter ```DOCKER_PASSWORD and value is <dockerPassword>```and click add.  
5. In the ```.travis.yml```file add this code.  
```
  # Log in to the docker cli
  # Get the password and emit over stdin as input to the next command(other side of the pipe).
  # We then run the login command and add the docer id and it can expect to recieve the password over stdin.
  - echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_ID" --password-stdin

  # Take all the build inamges and push them to docker hub
  - docker push bomarconi/multi-client
  - docker push bomarconi/multi-nginx
  - docker push bomarconi/multi-server
  - docker push bomarconi/multi-worker
```
6. Test the script by pushing the code to github.  
