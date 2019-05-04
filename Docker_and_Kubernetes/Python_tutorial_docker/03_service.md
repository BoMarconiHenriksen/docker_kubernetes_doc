# Service
En service kører et image, der er en lille del af en applikation.  
En applikation kan have mange services, og de kan skaleres så du får flere containere.  
### docker-compose.yml
```
version: "3"
services:
  web:
    # replace username/repo:tag with your name and image details
    image: username/repo:tag # Pull the image from the registry.
    deploy:
      replicas: 5 # Run 5 instances of that image as a service called web.
      resources:
        limits:
          cpus: "0.1" # limiting each one to use, at most, 10% of the CPU (across all cores).
          memory: 50M # limiting each one to use, at most, (across all cores), and 50MB of RAM.
      restart_policy:
        condition: on-failure # Immediately restart containers if one fails.
    ports:
      - "4000:80" # Map port 4000 on the host to web’s port 80.
    networks:
      - webnet # Instruct web’s containers to share port 80 via a load-balanced network called webnet. (Internally, the containers themselves publish to web’s port 80 at an ephemeral port.)
networks:
  webnet: # Define the webnet network with the default settings (which is a load-balanced overlay network).
```
### Run the new load-balancing app
```
docker swarm init
docker stack deploy -c docker-compose.yml getstartedlab
docker service ls
```
En enkelt container, der kører i en service kaldes en task.  
Få en liste med dine tasks.  
```
docker service ps getstartedlab_web
docker container ls -q
```
### Skaler din app
Du ændrer antallet af replicas, og redeployer.  
```
docker stack deploy -c docker-compose.yml getstartedlab
```
### Take down the app and the swarm
Appen.  
```
docker stack rm getstartedlab
```
The swarm.  
```
docker swarm leave --force
```



