# Container Port Mapping
A container has it's own isolated ports that can rescive trafic but by default no incomming trafic to your computer will be directed to the container.  
We have to setup a specif port mapping to get trafic to the container.  

Anytime someone makes a request to a port on your local network. Take that request and automaticaly forward it to a port inside the container.  

This is only for incomming requests. Your docker container can by default make requests to the outside world.  

### Setup docker run with port mapping
```docker run -p <route incoming requests to this port on local host to...> : <...this port inside the container> <image id or name>```
```docker run -p 8080:8080 bomarconi/simpleweb```
OBS! The ports does not have to be identical.  
> You can change the port inside the container just make sure the port that the application is listening to is changed.  
Go to localhost:8080  
