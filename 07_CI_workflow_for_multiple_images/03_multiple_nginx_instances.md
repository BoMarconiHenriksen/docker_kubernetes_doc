# Multiple Nginx Instances
We want to setup one Nginx infront of the servers to handle routes and another Nginx to serve the React App.  

### Altering Nginx's Listen Port
1. In the client folder make a new folder called nginx.  
2. In the nginx folder create a file called ```default.conf``` and add this code.  
```
server {
	listen 3000;

	location / {
		# Our production assets will be here.
		root /usr/share/nginx/html;
		index index.html index.htm;
		# For React router to work
		try_files $uri $uri/ /index.html;
	}
}
```
1. In the client directory create a ```Dockerfile```
2. Add this code to the file.  
```
FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .

# The build process. We get a folder called build. We have to copy that to nginx phase of our build
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# FRom builder copy /app/build to usr/share...
COPY --from=builder /app/build /usr/share/nginx/html
```
