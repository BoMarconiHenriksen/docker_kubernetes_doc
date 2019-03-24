# Docker Compose for Running Tests
Create a service that runs your test suits.  
1. If your app is running close it.  
2. In docker-compose.yml create a new service:  
```
tests:
    build: 
      context: .
      dockerfile: Dockerfile.dev
    volumes: 
      - /app/node_modules
      - .:/app
      # Overwrite the starting command when the test service is created.  
    command: ["npm", "run", "test"]
```
We now have 2 containers. One for the app and one for the tests.  
3. Sometimes when you add a new service you need to build first. ```docker-compose up --build```
4. Create a new test and check that the container update.  
> The downside is we get all the result from thetest inside the container so we cant rerun the tests.  
