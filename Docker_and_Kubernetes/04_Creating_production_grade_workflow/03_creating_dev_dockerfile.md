# Creating the Dev Dockerfile
We want 2 Dockerfile for the frontend. One for development and one for production.  
##### We are going to start with the Dockerfile for development.  
1. In the frontend folder create a file called: ```Dockerfile.dev```  
2. Add this to the Dockerfile.dev  
```
FROM node:alpine

WORKDIR '/app'

COPY package.json .
RUN npm install

COPY . .

CMD ["npm", "run", "start"]
```
3. Run a Dockerfile with a custom file name: ```docker build -f Dockerfile.dev .```  
4. ```docker run -p 3000:3000 <containerId>```
5. In app.js in the p tag change the text.  
