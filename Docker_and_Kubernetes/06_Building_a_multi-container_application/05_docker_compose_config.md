# Docker Compose Config
Add Redis service to the docker-compose file.  
1. In the root directory of the project go to your docker-compose.yml file.  
2. Add redis service to the file.  
```
redis:
    image: 'redis:latest'
```
3. Add a server to the docker-compose file.  
```
server:
    build: 
    dockerfile: Dockerfile.dev
    # Look in the server folder and use that folder to build.
    context: ./server
  volumes:
    # Leave this folder as it is in the container.
    - /app/node_modules
    # Look in the server directory and copy all of the content to /app in the container
    - ./server:/app
```
