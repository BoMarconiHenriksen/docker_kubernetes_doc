# Volumes
Docker volumes is a placeholder inside the docker container.  
We will set up a volume that points back with a reference to our local machine.  
That will give us access to the files and folders on the local machine. 
We then don't have to copy the files and folders to the docker container.  
You can think of it in the same way as port mapping.  
##### the command is
```docker run -p 3000:3000 <put a bookmark on the node_modules folder> <map the pwd into the '/app' folder>```  
```docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <imageId>```
```-v $(pwd):/app``` -> We want to map up a folder inside a container to a folder outside the container.  
```-v /app/node_modules``` -> We want this to be a placeholder inside a container. Do not map it up with anything.  

1. First rebuild your image: ```docker build -f Dockerfile.dev .```
2. ```docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <imageId>```
When you change source code it will be reflected in the browser.  
### Shorthand with docker-compose
1. In the root add a docker-compose.yml file.  
2. Add this code to the file.  
```
version: '3'
services: 
  web:
    build: .
    ports: 
      - "3000:3000"
    volumes: 
      - /app/node_modules
      - .:/app # the curent folder outside the container( . ) to the folder inside the container(/app).
```
3. docker-compose up  
This will not work because it's a docker.dev file.  
