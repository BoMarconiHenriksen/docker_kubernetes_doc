# Applying a Deployment
1. kubectl get pods  
##### How can we delete the existing pod before adding the new?
To do that we are going to use the config file that was used to create it.  
delete - delete a running object.  
2. ```kubectl delete -f client-pod.yaml```  
3. ```kubectl get pods``` --> no running pods.  
4. ```kubectl apply -f client-deployment.yaml```  
5. ```kubectl get pods```  
6. ```kubectl get deployments``` # Get the status of deployments.  
If you change the template uptodate will go down to 0 when change to the new configuration.  
