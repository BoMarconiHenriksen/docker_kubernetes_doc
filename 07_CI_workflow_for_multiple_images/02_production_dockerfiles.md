# Production Dockerfiles
1. Go to worker directory and create a ```Dockerfile```
2. Add this code to the file.  
```
FROM node:alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run", "start"]
```
1. In the server directory create a ```Dockerfile```
2. Add this code to the file.  
```
FROM node:alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run", "start"]
```
1. In the nginx directory create a ```Dockerfile```
2. Add this code to the file.  
```
FROM nginx
# Take our file and overwrite the existing one in the container.
COPY ./default.conf /etc/nginx/conf.d/default.conf
```
1. In the client directory create a ```Dockerfile```
2. Add this code to the file.  
```

```
