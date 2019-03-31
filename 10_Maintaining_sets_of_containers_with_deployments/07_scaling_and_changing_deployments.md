# Scaling and Changing Deployments
Lets see if it's possible to update the port with the deployment object.  
1. Go to client-deployment.yaml and update the containerPort to 9999  
2. ```kubectl apply -f client-deployment.yaml```  
3. ```kubectl get deployments```  
4. ```kubectl get pods``` # You can see that it's a new pod.  
> Deleted the pod and created a new with port 9999.  
Check that it is using port 9999.  
5. ```kubectl describe pods```  
##### scale up with replicas
6. Change replicas to 5.  
7. ```kubectl apply -f client-deployment.yaml```  
8. ```kubectl get deployments```  
9. ```kubectl get pods```  
##### Change the image to multi-worker
10. ```kubectl apply -f client-deployment.yaml```  
11. ```kubectl get deployments```  
