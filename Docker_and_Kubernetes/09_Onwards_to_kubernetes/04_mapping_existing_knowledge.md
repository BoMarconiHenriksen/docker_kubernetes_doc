# Mapping Existing Knowledge
To check that minikube is running write ```minikube status```  
Check that kubectl is working ```kubectl cluster-info```  
Goal is: To get the multi-client image running on our local Kubernetes cluster running as a container.  
For the docker-compose file...  
... each entry(service) can optionally get docker-compose to build an image.  
... each entry(service) represents a container we want to create.  
... each entry(service) defines the networking requirements(ports).  
```
service:
	nginx:
		build:
		ports:
```
#### Going from docker-compose to Kubernetes:  
1. each entry(service) can optionally get docker-compose to build an image --> Kubernetes expects all images to already be build.  
2. each entry(service) represents a *container* we want to create --> Kubernetes: One config file per *object* we want to create.  
3. each entry(service) defines the networking requirements(ports) --> we have to manually set up all networking.  
#### Get a simple container running on our local Kubernetes Cluster running
1. Kubernetes expects all images to already be build --> Make sure our image is hosted on docker hub.  
2. One config file per *object* we want to create --> Make one config file to create the container.  
3. We have to manually set up all networking --> Make one config file to set up networking.  
