# Troubleshooting
Hi!  Its entirely possible that you might run into a bug or two when you start up this set of containers with docker-compose.  

Are you able to enter a number into the react app, but it appears to never be calculated, as seen in this screenshot?  

If that's the case, then you can try adding in environment variables to the 'worker' entry in the docker-compose file, like so:  
```
worker:  
  environment:
    - REDIS_HOST=redis
    - REDIS_PORT=6379
```
Then restart docker-compose.  

The next section also has a couple of other possible troubleshooting tips.  
