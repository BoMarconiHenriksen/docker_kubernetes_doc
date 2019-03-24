# Opening Websocket Connection
The app wants an active connection to the React server so it updates instantly.  
1. Open default.conf file.  
2. Add this code in the server blok.
```
location /sockjs-node {
    proxy_pass http://client;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "Upgrade";
}
```
3. ```docker-compose up --build```
