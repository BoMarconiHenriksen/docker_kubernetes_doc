# Adding Postgres as a Service
For the compose file we need to add postgres, redis and server services.  
We'll start with Postgress.  
1. In the root directory of the project add a docker-compose.yml file.  
2. Add this to the file.  
```
version: '3'
services: 
  # The name of the postgres instance.
  postgress:
    image: 'postgres:latest'
```
3. cd to complex folder.  
4. docker-compose up  
