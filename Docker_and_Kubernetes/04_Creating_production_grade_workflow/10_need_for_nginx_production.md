# Need for Nginx
We are going to make a production container with an Nginx server.  
### Multi-Step Bocker Builds
The new Dockerfile is going to be for production.  
We are going to do 2 phases in the Dockerfile. First we have a build phase and then we have a run phase.  
The build is going to be created in the working directory /app/build.  
1. In root create a Dockerfile.  
2. Add this code to the Dockerfile.
```
# Build phase using a tag.
FROM node:alpine as builder 
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
# The build is going to be created in the working directory /app/build  
RUN npm run build

# Run phase
# The new FROM statement is terminating the previous blok(the other FROM statement).
FROM nginx
# Copy build folder from a diffrent phase and copy build to nginx
# With the COPY statement we will drop all the other stuff from the build phase. So the container will only have nginx and the build we copied.
COPY --from=builder /app/build /usr/share/nginx/html
```
### Running Production Dockerfile
1. ```docker build .```
2. ```docker run -p 8080:80 <containerId>```
3. Go to localhost:8080  
