# Run application in Azure Kubernetes Service(AKS)
Kubernetes provides a distributed platform for containerized applications. You build and deploy your own applications and services into a Kubernetes cluster, and let the cluster manage the availability and connectivity. In this tutorial, part four of seven, a sample application is deployed into a Kubernetes cluster. You learn how to:  

Update a Kubernetes manifest files  
Run an application in Kubernetes  
Test the application  
### Update the manifest file
In these tutorials, an Azure Container Registry (ACR) instance stores the container image for the sample application. To deploy the application, you must update the image name in the Kubernetes manifest file to include the ACR login server name.  

Get the ACR login server name using the az acr list command as follows:  
```
az acr list --resource-group myResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```
The sample manifest file from the git repo cloned in the first tutorial uses the login server name of microsoft. Make sure that you're in the cloned azure-voting-app-redis directory, then open the manifest file azure-vote-all-in-one-redis.yaml.  
Replace microsoft with your ACR login server name. The image name is found on line 47 of the manifest file. The following example shows the default image name:  
```
containers:
- name: azure-vote-front
  image: microsoft/azure-vote-front:v1
```
Provide your own ACR login server name so that your manifest file looks like the following example:  
```
containers:
- name: azure-vote-front
  image: <acrName>.azurecr.io/azure-vote-front:v1
```
### Deploy the application
To deploy your application, use the kubectl apply command. This command parses the manifest file and creates the defined Kubernetes objects. Specify the sample manifest file, as shown in the following example:  
```
kubectl apply -f azure-vote-all-in-one-redis.yaml
```
### Test the application
When the application runs, a Kubernetes service exposes the application front end to the internet. This process can take a few minutes to complete.  

To monitor progress, use the kubectl get service command with the --watch argument.  
```
kubectl get service azure-vote-front --watch
```
Initially the EXTERNAL-IP for the azure-vote-front service is shown as pending.  
When the EXTERNAL-IP address changes from pending to an actual public IP address, use CTRL-C to stop the kubectl watch process. The following example output shows a valid public IP address assigned to the service.  
To see the application in action, open a web browser to the external IP address of your service.  
If the application didn't load, it might be due to an authorization problem with your image registry. To view the status of your containers, use the kubectl get pods command. If the container images can't be pulled, see allow access to Container Registry with a Kubernetes secret. https://docs.microsoft.com/en-us/azure/container-registry/container-registry-auth-aks#access-with-kubernetes-secret  
