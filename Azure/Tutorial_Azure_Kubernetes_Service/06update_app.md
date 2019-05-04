# Update an application in Azure Kubernetes Service
After an application has been deployed in Kubernetes, it can be updated by specifying a new container image or image version. An update is staged so that only a portion of the deployment is updated at the same time. This staged update enables the application to keep running during the update. It also provides a rollback mechanism if a deployment failure occurs.  

In this tutorial, part six of seven, the sample Azure Vote app is updated. You learn how to:  

Update the front-end application code  
Create an updated container image  
Push the container image to Azure Container Registry  
Deploy the updated container image  
### Update an application
Let's make a change to the sample application, then update the version already deployed to your AKS cluster. Make sure that you're in the cloned azure-voting-app-redis directory. The sample application source code can then be found inside the azure-vote directory. Open the config_file.cfg file with an editor, such as vi:  
```
azure-vote/azure-vote/config_file.cfg
```
Change the values for VOTE1VALUE and VOTE2VALUE to different values, such as colors. The following example shows the updated values:  
```
# UI Configurations
TITLE = 'Azure Voting App'
VOTE1VALUE = 'Blue'
VOTE2VALUE = 'Purple'
SHOWHOST = 'false'
```
Save and close the file.  
### Update the container image
To re-create the front-end image and test the updated application, use docker-compose. The --build argument is used to instruct Docker Compose to re-create the application image:  
```
docker-compose up --build -d
```
This is done locally so check the changes at http://localhost:8080  
### Tag and push the image
To correctly use the updated image, tag the azure-vote-front image with the login server name of your ACR registry. Get the login server name with the az acr list command:  
```
az acr list --resource-group myResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```
Use docker tag to tag the image. Replace `<acrLoginServer>` with your ACR login server name or public registry hostname, and update the image version to :v2 as follows:  
```
docker tag azure-vote-front <acrLoginServer>/azure-vote-front:v2
```
Now use docker push to upload the image to your registry. Replace `<acrLoginServer>` with your ACR login server name. If you experience issues pushing to your ACR registry, make sure that you have run the az acr login command.  
Remember to login first: `az acr login --name <acrname>`
```
docker push testen.azurecr.io/azure-vote-front:v2
```
# Deploy the updated application
To provide maximum uptime, multiple instances of the application pod must be running. Verify the number of running front-end instances with the kubectl get pods command:  
```
kubectl get pods
```
If you don't have multiple front-end pods, scale the azure-vote-front deployment as follows:  
```
kubectl scale --replicas=3 deployment/azure-vote-front
```
To update the application, use the kubectl set command. Update `<acrLoginServer>` with the login server or host name of your container registry, and specify the v2 application version:  
```
kubectl set image deployment azure-vote-front azure-vote-front=<acrLoginServer>/azure-vote-front:v2
```
To monitor the deployment, use the kubectl get pod command. As the updated application is deployed, your pods are terminated and re-created with the new container image.  
```
kubectl get pods
```
### Test the updated application
To view the update application, first get the external IP address of the azure-vote-front service:  
```
kubectl get service azure-vote-front
```
