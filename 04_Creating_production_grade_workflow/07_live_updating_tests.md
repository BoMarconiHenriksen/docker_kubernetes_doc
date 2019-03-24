# Live Updating Tests
The problem with executing tests is that it does not update when we write a new test.  
There are two ways to solve this. We'll start with a solution without using volume.  
1. ```docker-compose up```  
We can attach to the existing container that is created. When we are attaced to it we can then execute a command that start up the test suite. We can do this because we alrady have the volume setup  
2. Open a secound terminal window.  
3. Get the id of the running container. ```docker ps```  
4. Execute a new command inside the container. ```docker exec -it <idOfRunningContainer> npm run test
5. Delete the 2. test and go back to the termial and check that you only have 1 test.  
> This is not the best solution because you need to remember to get the id of the running container and execute the docker exec command.
