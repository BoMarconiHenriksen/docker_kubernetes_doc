# Nginx Path Routing
We have not done any port mapping(nothing is exposed to the outside world) and that is because of nginx thats placed in front of the app.  
We are going to use Nginx to route to diffrent servers.  
Nginx is placed in a server and is going to look at the request path. /api is routed to express server and a / is going to the React server.  
We did not use ports because in a production envirinment we dont have to worry about ports. The ports can easy change.  
### Routing with Nginx
We are going to add a file called default.conf. The file adds configuration to Nginx.
We have to tell Nginx that:
1. There is an *upstream* server at client:3000 (Nginx calls it upstream because the server is behind Nginx. You can not access them unless you go through Nginx)  
2. There is an *upstream* server at server:5000  
3. Listen on port 80
4. If anyone comes to ```'/'``` send them to client upstream.  
5. If anyone comes to ```'/api'``` send them to server upstream.  
Let's get started.  
1. In the root folder create a folder call nginx.  
2. In the nginx folder create a file called default.conf
3. Add this code to the file.  
```
# There is an upstream.  
upstream client {
    # The upstream is located at and this is how to access it.
    server client:3000; 
}

# Chenge line 8 in the docker-compose file to api
upstream api {
    server api:5000;
}

server {
    listen 80;

    location / {
        proxy_pass http://client;
    }

    location /api {
        # Trims of the first api part.
        rewrite /api/(.*) /$1 break;
        proxy_pass http://api;
    }
}
```
