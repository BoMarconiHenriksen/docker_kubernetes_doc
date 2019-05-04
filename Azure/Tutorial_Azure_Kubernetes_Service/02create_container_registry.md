# Deploy and use Azure Container Registry
Azure Container Registry (ACR) is a private registry for container images. A private container registry lets you securely build and deploy your applications and custom code. In this tutorial, part two of seven, you deploy an ACR instance and push a container image to it. You learn how to:  

Create an Azure Container Registry (ACR) instance  
Tag a container image for ACR  
Upload the image to ACR  
View images in your registry  
In additional tutorials, this ACR instance is integrated with a Kubernetes cluster in AKS, and an application is deployed from the image.  
```
az login
```
### Create an Azure Container Registry
To create an Azure Container Registry, you first need a resource group. An Azure resource group is a logical container into which Azure resources are deployed and managed.  

Create a resource group with the az group create command. In the following example, a resource group named myResourceGroup is created in the eastus region:  
```
az group create --name myResourceGroup --location eastus
```
Create an Azure Container Registry instance with the az acr create command and provide your own registry name. The registry name must be unique within Azure, and contain 5-50 alphanumeric characters. In the rest of this tutorial, <acrName> is used as a placeholder for the container registry name. Provide your own unique registry name. The Basic SKU is a cost-optimized entry point for development purposes that provides a balance of storage and throughput.  
```
az acr create --resource-group myResourceGroup --name <acrName> --sku Basic
```
### Log in to the container registry
To use the ACR instance, you must first log in. Use the az acr login command and provide the unique name given to the container registry in the previous step.  
```
az acr login --name <acrName>
```
### Tag a container image
To see a list of your current local images, use the docker images command:  
```
docker images
```
To use the azure-vote-front container image with ACR, the image needs to be tagged with the login server address of your registry. This tag is used for routing when pushing container images to an image registry.  

To get the login server address, use the az acr list command and query for the loginServer as follows:  
```
az acr list --resource-group myResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```
Now, tag your local azure-vote-front image with the acrloginServer address of the container registry. To indicate the image version, add :v1 to the end of the image name:  
```
docker tag azure-vote-front <acrLoginServer>/azure-vote-front:v1
```
To verify the tags are applied, run docker images again. An image is tagged with the ACR instance address and a version number.  
```
docker images
```
### Push images to registry
With your image built and tagged, push the azure-vote-front image to your ACR instance. Use docker push and provide your own acrLoginServer address for the image name as follows:  
```
docker push <acrLoginServer>/azure-vote-front:v1
```
### List images in registry
To return a list of images that have been pushed to your ACR instance, use the az acr repository list command. Provide your own <acrName> as follows:  
```
az acr repository list --name <acrName> --output table
```
To see the tags for a specific image, use the az acr repository show-tags command as follows:  
```
az acr repository show-tags --name <acrName> --repository azure-vote-front --output table
```
You now have a container image that is stored in a private Azure Container Registry instance. This image is deployed from ACR to a Kubernetes cluster in the next tutorial.  

###
In this tutorial, you created an Azure Container Registry and pushed an image for use in an AKS cluster. You learned how to:  

Create an Azure Container Registry (ACR) instance  
Tag a container image for ACR  
Upload the image to ACR  
View images in your registry  

Advance to the next tutorial to learn how to deploy a Kubernetes cluster in Azure.  
