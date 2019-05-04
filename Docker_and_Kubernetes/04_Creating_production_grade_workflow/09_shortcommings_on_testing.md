# Shortcomings on Testing
The reason why we can't type anything in the terminal is that stdin is not setup by default.  
This is difficult to setup with docker compose.  
What we can do is to open a secound terminal window and run the docker attach command.  
With attact we can forward input to a specific container.  
1. Get the container id for the npm run start container. ```docker ps```  
2. ```docker attach <containerId>```
Unfortunately this is not going to work.
When we use attach we always connect to the primary process of the container and the test is not the primary process.  
