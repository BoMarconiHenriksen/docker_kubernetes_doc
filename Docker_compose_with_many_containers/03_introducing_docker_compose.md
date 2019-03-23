# Introducing Docker Compose
We can run our image.  
```docker run bomarconi/visits  ```
We get an error because we have not made the redis container.  
Get the Redis server.  
```docker run redis```
We need to make a network between the 2 containers. For that we have 2 options.  
1. We can use docker cli but it's a pain in the neck to do...
2. We can use docker compose.

What is docker compose?  
1. It's a seperate cli already installed on your machine.  
2. Used to start up multiple Docker containers at the same time.  
3. Automate some of the long arguments we were passing to docker run.  
