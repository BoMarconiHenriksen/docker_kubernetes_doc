# Building a Custom Nginx Image
Find Nginx on docker hub for settings.  
1. In the nginx folder create a file called Dockerfile.dev  
2. Add this code to the file.  
```
FROM nginx
# Take our file and overwrite the existing one in the container.
COPY ./default.conf /etc/nginx/conf.d/default.conf
```
3. Add an Nginx service to the docker-compose.yml file.  
4. Add this to the file.  
```
nginx:
    # Always has to run because it's routing our app so we add a restart policy.
    restart: always
    build: 
      dockerfile: Dockerfile.dev
      context: ./nginx
    ports: 
      - '3050:80'
```
5. Test it(there is a good chance that the first time we run it) ```docker-compose up --build```
