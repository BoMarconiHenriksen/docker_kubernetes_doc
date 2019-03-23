# Building a Dockerfile
Create an image that runs redis-server.  
1. mkdir redis-image
2. cd redis-image
3. code .
4. Create a new file called(with no extension): ```Dockerfile```
```
# Use an existing docker image as a base.
FROM alpine

# Download and install a dependency.
RUN apk add --update redis

# Tell the image what to do when it starts as a container.
CMD ["redis-server"]
```
5.In the command line write: ```docker build .```
6. ```docker run <container id>```
### Explanation
#### FROM
What image do we want to use as a base.  
#### RUN
Execute commands while we are preparing the image.  
#### CMD (Command Instruction)
What should be executed when our image is used to start up a new container.  






