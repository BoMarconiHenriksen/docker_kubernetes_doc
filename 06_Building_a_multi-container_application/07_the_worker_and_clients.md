# The Worker and Client Service
We have to add services for the client and worker.  
1. In the docker-compose file add this code.  
```
client:
    build: 
      dockerfile: Dockerfile.dev
      context: ./client
    volumes:
      - /app/node_modules
      - ./client:/app
  worker:
    build: 
      dockerfile: Dockerfile.dev
      context: ./worker
    volumes: 
      - /app/node_modules
      - ./worker:/app
```
