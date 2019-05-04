# Executing Tests
Running tests in the container for the developer enviroment.  
1. Get the container id: ```docker build -f Dockerfile.dev .```  
2. Execute the tests: ```docker run <containerId> npm run test```
3. To interact with the test menu: ```docker run -it <containerId> npm run test```
