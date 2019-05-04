# Single Container Deployment Issues
1. The app was simple - no outside dependencies.  
2. Our image was build multiple times.  
3. How do we connect to a database from a container.  
### Application Overview
We are going to build a fancy overcomplicated fibernati calculator.  
### Application Architure
Nginx webserver routing to react server(frontend) or express server(backend api).  
Redis as in memory datastore.  
Postgres as database.  
Worker watch redis for new indexs and calculate the value.  

We want to make Dockerfiles for the React app, Express server and the worker.  



