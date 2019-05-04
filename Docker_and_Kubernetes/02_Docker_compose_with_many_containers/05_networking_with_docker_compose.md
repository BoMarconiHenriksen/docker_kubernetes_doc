# Networking with Docker Compose
When the 2 containers are created with docker-compose we dont need to specify network. It's created automatically.  

The port connection we made is only to open up access to our container on our local machine.  
Add the redis-server location to the index.js. Use the name it was given in the docker-compose.yml file.  
```
const client = redis.createClient({
  host: 'redis-server',
  port: 6379 // We don't need to add a port.
});
```
When the request goes out docker is going to see it's looking for a host called redis-server and then connect to that container.  
