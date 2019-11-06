```
docker build -t friendlyhello .  # Create image using this directory's Dockerfile.
docker build -f Dockerfile.dev . # Build a Dockerfile with a custom name.  

docker run -p 4000:80 friendlyhello  # Run "friendlyname" mapping port 4000 to 80.
docker run -d -p 4000:80 friendlyhello         # Same thing, but in detached mode.
docker run username/repository:tag                   # Run image from a registry . 
docker run <image name> <command> Eks. docker run bustbox ls   # Default command in image is not going to be executed.  
docker run -it <image name> sh # Open a terminal in the docker container. Can't run any other process. For that use docker exec.  
docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app imageId # Setup a volume a reference.  
docker run <containerId> npm run test # Run test manually for a Node app.  
docker run -it <containerId> npm run test # Run test manually and interact with the test menu.  

docker ps # List all running containers on your machine.
docker ps --all # List all the containers we have created.

docker stop $(docker ps -a -q) # Stop all running containers.  
docker system prune # Delete all containers locally.  

docker logs <container id> # Get logs/output from inside a container.  

docker stop <container id> # Stop a process inside the container. Cleanup before container stops.  
docker kill <container id> # Shut down right now. No cleanup.  Use if container has locked up.  

docker exec -it <container id> <command to execute> # Execute command in container.  
docker exec -it <container id> sh # Open a shell inside the container to get full terminal access. ctrl + d to exit  

docker container ls                                # List all running containers.
docker container ls -a             # List all containers, even those not running.
docker container stop <hash>           # Gracefully stop the specified container.
docker container kill <hash>         # Force shutdown of the specified container.
docker container rm <hash>        # Remove specified container from this machine.
docker container rm $(docker container ls -a -q)         # Remove all containers.

docker image ls -a                             # List all images on this machine.
docker image rm <image id>            # Remove specified image from this machine.
docker image rm $(docker image ls -a -q)   # Remove all images from this machine.

docker login             # Log in this CLI session using your Docker credentials.
docker tag <image> username/repository:tag  # Tag <image> for upload to registry.
docker push username/repository:tag            # Upload tagged image to registry.

```
### Service
```
docker stack ls                                            # List stacks or apps.
docker stack deploy -c <composefile> <appname>  # Run the specified Compose file.
docker service ls                 # List running services associated with an app.
docker service ps <service>                  # List tasks associated with an app.
docker inspect <task or container>                   # Inspect task or container.
docker container ls -q                                      # List container IDs.
docker stack rm <appname>                             # Tear down an application.
docker swarm leave --force      # Take down a single node swarm from the manager.
```
### Swarms
```

```
