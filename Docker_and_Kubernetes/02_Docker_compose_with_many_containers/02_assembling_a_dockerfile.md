# Assembling a Dockerfile
We start to create a Dockerfile for the Node application.  
1. Create a Dockerfile in the visits folder.  
2. Add this code to the Dockerfile.  
```
FROM node:alpine

WORKDIR '/app'

COPY package.json .
RUN npm install
COPY . .

CMD ["npm", "start"]
```
3. docker build .
4. docker build -t bomarconi/visits:latest .
