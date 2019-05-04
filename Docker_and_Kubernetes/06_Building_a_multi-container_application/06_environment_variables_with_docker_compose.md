# Environment Variables with Docker Compose
We are going to customize how the server behaives when it is started up as a container.  
##### Syntax
variableName=value # Sets a variable in the container at *run time* of the container.  
variableName # Sets a variable in the container at *run time*. The value is taken from *your computer*. Used to secret keys  
> Use docker hub to find ports and default password, user names and databases.  
1. Add this to the docker-compose.yml file.
```
environment:
    # We don't specify the ip to the service just the name of the service.
    - REDIS_HOST=redis
    # Find the port at docker hub
    - REDIS_PORT=6379
    - PGUSER=postgres
    - PGHOST=postgres
    - PGDATABASE=postgres
    # Find the default password at docker hub
    - PGPASSWORD=postgres_password
    - PGPORT=5432
```
2. Test it with ```docker-compose up```
