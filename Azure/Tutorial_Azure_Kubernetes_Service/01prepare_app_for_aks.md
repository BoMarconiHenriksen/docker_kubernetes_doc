# Prepare Application for AKS
Docker Compose can be used to automate building container images and the deployment of multi-container applications.  
Use the sample docker-compose.yaml file to create the container image, download the Redis image, and start the application:  
```
docker-compose up -d
```
See the images.    
```
docker images
```
Run the docker ps command to see the containers.  
```
docker ps
```
To see the running application, enter http://localhost:8080 in a local web browser.  
Now that the application's functionality has been validated, the running containers can be stopped and removed. Do not delete the container images - in the next tutorial, the azure-vote-front image is uploaded to an Azure Container Registry instance.  

Stop and remove the container instances and resources with the docker-compose down command:  
```
docker-compose down
```
When the local application has been removed, you have a Docker image that contains the Azure Vote application, azure-front-front, for use with the next tutorial.  
