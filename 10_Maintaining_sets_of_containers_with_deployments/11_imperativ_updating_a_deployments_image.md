# Imperativly Updatin a Deployment's Image
1. Tag the image with a new version number, push to docker hub.  
2. Run a kubectl command forcing the deployment to use the new image version.  
---  
1. Open a new terminal window and cd into the client directory(multi-docker/client).  
2. docker build -t bomarconi/multi-client:v5 .  
3. docker push bomarconi/multi-client:5  
```kubectl set image <object_type> / <obejct_name> <container_name> = <new_image_to_use>```
*set* = we want to change a property in one of the objects inside the cluster.  
*image* = we want to change the image property.  
*object_type* = type of object.  
*object_name* = name of the object.  
*container_name* = Name of the container we are updating(get this from config file).  
*new_image_to_use* = full name of image to use withtag.  
4. ```kubectl set image deployment/client-deployment client=bomarconi/multi-client:5``` (is done in the folder where your client-deployment.yaml file is)  
5. kubectl get pods  
6. Check the change in the browser.  
> Create a script for this.  
