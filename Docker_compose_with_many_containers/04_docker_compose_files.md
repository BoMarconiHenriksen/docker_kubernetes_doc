# Docker Compose files
We put our ```docker build -t bomarconi/visits:latest``` and ```docker run -p 8080 bomarconi/visits``` into a docker-compose.yml file.  

So basically docker-compose.yml contains all the options we'd normallywrite in docker-cli.  

We'll tell docker-compose.yml that we want to create:  
1. redis-server  
⋅⋅1. Make it use 'redis' image.  
2. node-app  
⋅⋅2. Make it use the Dockerfile in the current directory.  
⋅⋅2. Map port 8081 to 8081.  

1. In the visits folder create a docker-compose.yml file.  
2. copy paste this code into the file.  
```
# The version of docker-compose we are going to use.
version: '3'

# Tell docker-compose here is what we want to do.
# Services is a type of a container.
services:
  # Ower first container.
  redis-server:
    image: 'redis'
  node-app:
    # Look for a Dockerfile in the curent folder and build it.
    build: .
    # The ports we want to open up for this container.
    ports: 
      # - specifies an array in yml file.
      # Local machine:container
      - "4001:8081"
```
