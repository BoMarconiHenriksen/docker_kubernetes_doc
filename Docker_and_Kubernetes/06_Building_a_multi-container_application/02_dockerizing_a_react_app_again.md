# Dockerizing a React App Again
We are focusing on development so we will have dev Dockerfiles for each container.  
We want to be sure that when you cange code you don't have to rebuild the entire image every time to get the changes take effect.  
This is our plan:  
1. Copy over package.json  
2. Run npm install  
3. Copy over everything else  
4. Docker compose should set up a volume to 'share' files.  
Let's get started!
1. In the root of the client folder make a new file called Dockerfile.dev  
2. Add this code to the file.  
```
FROM node:alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run", "start"]
```
3. cd to client directory.  
4. Test it with ```docker build -f Dockerfile.dev .```
5. ```docker run <containerId>```
