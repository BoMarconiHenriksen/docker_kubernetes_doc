# Dockerizing Generic Node Apps
1. In the root of the server folder create a Dockerfile.dev file.  
2. Add this code.  
```
FROM node:alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run", "dev"]
```
Do the exact same for the worker directory.  
3. cd into server.  
4. docker build -f Dockerfile.dev .
5. ```docker run <containerId>```
6. cd into worker.  
7. docker build -f Dockerfile.dev .
8. ```docker run <containerId>```
