# Manual Generation with Docker Commit
You can take a container. Change it and then create an image manually(this is not done very often).  
This is the manual version of a Dockerfile.  

1. docker run -it alpine sh
2. Inside the container: ```apk add --update redis```
3. Open a new terminal.    
4. Take a snapshot of the running container, add a default command and create an image of it:
```
docker commit -c '["redis-server"]' <id of running container>
docker run <id of the image that was just created>
```
