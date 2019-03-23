# Automatic Container Restarts
### Define a restart policie
'no' - Never attempt to restart this . container if it stops or crashes. This is default.  
always - If the container stops *for any reason* always attempt to restart it.  
on-failure - Only restart if the container stops with an error code.  
unless-stopped - Always restart unless we(the developers) forcibly stop it.  

In the docker-compose.yml file under node-app add.
```restart: always```

```docker-compose up``` when you visit the page it will show an error.  
Go to the terminal and check that the server exit with code 0 and then starts up again.  

If you are running a webserver use the always policy and if you are running a worker process(processing a file ect) then use on-failure because when it has finished it's job it will close down. 
   