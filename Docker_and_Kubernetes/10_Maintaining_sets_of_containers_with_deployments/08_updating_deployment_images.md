# Updating Deployment Images
How to update a deployment when a new version of an image becomes avaible?  
1. Change deployment to use multi-client again.  
2. Update the multi-client image, push to docker hub.  
3. Get the deployment to recreate our pods with the latest version of multi-client.  
---  
1. Go to client-deployment.yaml and chang replicas to 1.  
2. Change to image to multi-client and change the containerPort to 3000.  
3. ```kubectl apply -f client-deployment.yaml```
4. Open your browser and test that you can connect.  
