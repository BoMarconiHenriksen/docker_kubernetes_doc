# Quick Guide AKS Tutorial part 1 to 7
##### See he tutorial for indepth explanations
Create your containers locally.  
---
## Part 2
```
az login
```
### Create an Azure Container Registry
```
az group create --name myResourceGroup --location westeurope

az acr create --resource-group myResourceGroup --name <acrName> --sku Basic
```
### Log in to the container registry
```
az acr login --name <acrName>
```
### Get the login server address
```
az acr list --resource-group myResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```
### Tag a image 
```
docker tag azure-vote-front <acrLoginServer>/azure-vote-front:v1

docker images
```
### Push images to registry
```
docker push <acrLoginServer>/azure-vote-front:v1
```
### List images in registry
```
az acr repository list --name <acrName> --output table
```
To see the tags for a specific image, use the az acr repository show-tags command as follows:  
```
az acr repository show-tags --name <acrName> --repository azure-vote-front --output table
```
---
## Part 3
# Deploy an Azure Kubernetes Service(AKS) cluster
### Create a service principal
```
az ad sp create-for-rbac --skip-assignment
```
Make a note of the appId and password. These values are used in the following steps.  
### Configure ACR authentication
```
az acr show --resource-group myResourceGroup --name <acrName> --query "id" --output tsv
```
### Grant the access for the AKS cluster to pull images stored in ACR 
```
az role assignment create --assignee c0e71272-32cf-4761-a882-90c6cda47a01 --scope /subscriptions/8b5860ac-c7cf-4086-a05c-63f9ebab0085/resourceGroups/myResourceGroup/providers/Microsoft.ContainerRegistry/registries/testen --role acrpull
```
### Create a Kubernetes cluster
```
az aks create \
    --resource-group myResourceGroup \
    --name myAKSCluster \
    --node-count 1 \
    --service-principal <appId> \
    --client-secret <password> \
    --generate-ssh-keys
```
In one line and remove all the `\`.  
After a few minutes, the deployment completes, and returns JSON-formatted information about the AKS deployment.  
### Install the Kubernetes CLI
To connect to the Kubernetes cluster from your local computer, you use kubectl, the Kubernetes command-line client. https://kubernetes.io/docs/reference/kubectl/kubectl/   

If you use the Azure Cloud Shell, kubectl is already installed. You can also install it locally using the az aks install-cli command:  
```
az aks install-cli
```
### Connect to cluster using Kubectl
```
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
```
### Verify the connection to your cluster
```
kubectl get nodes
```
---
## Part 4
# Run application in Azure Kubernetes Service(AKS)
Update a Kubernetes manifest files  
Run an application in Kubernetes  
Test the application  
### Update the manifest file
### Get the ACR login server name 
```
az acr list --resource-group myResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```
### Provide ACR login to k8s manifest file
```
containers:
- name: azure-vote-front
  image: <acrName>.azurecr.io/azure-vote-front:v1
```
### Deploy the application
```
kubectl apply -f azure-vote-all-in-one-redis.yaml
```
### Test the application
```
kubectl get service azure-vote-front --watch
```
---
## Part 5
# Scale application in Azure Kubernetes Service
If you've followed the tutorials, you have a working Kubernetes cluster in AKS and you deployed the sample Azure Voting app. In this tutorial, part five of seven, you scale out the pods in the app and try pod autoscaling. You also learn how to scale the number of Azure VM nodes to change the cluster's capacity for hosting workloads. You learn how to:  

Scale the Kubernetes nodes  
Manually scale Kubernetes pods that run your application  
Configure autoscaling pods that run the app front-end  
### Manuall scale pods
When the Azure Vote front-end and Redis instance were deployed in previous tutorials, a single replica was created. To see the number and state of pods in your cluster, use the kubectl get command as follows:  
```
kubectl get pods
```
To manually change the number of pods in the azure-vote-front deployment, use the kubectl scale command. The following example increases the number of front-end pods to 5:  
```
kubectl scale --replicas=5 deployment/azure-vote-front
```
### Autoscale pods
Kubernetes supports horizontal pod autoscaling to adjust the number of pods in a deployment depending on CPU utilization or other select metrics. The Metrics Server is used to provide resource utilization to Kubernetes, and is automatically deployed in AKS clusters versions 1.10 and higher. To see the version of your AKS cluster, use the az aks show command, as shown in the following example.  
### AKS clusters version
```
az aks show --resource-group myResourceGroup --name myAKSCluster --query kubernetesVersion
```
### CPU Request and Limits for Autoscaler
```
resources:
  requests:
     cpu: 250m
  limits:
     cpu: 500m
```
### kubectl autoscale command
```
kubectl autoscale deployment azure-vote-front --cpu-percent=50 --min=3 --max=10
```
### Status of the autoscaler,
```
kubectl get hpa
```
After a few minutes, with minimal load on the Azure Vote app, the number of pod replicas decreases automatically to three. You can use kubectl get pods again to see the unneeded pods being removed.  
### Manually scale AKS nodes
```
az aks scale --resource-group myResourceGroup --name myAKSCluster --node-count 3
```
---  
## Part 6 - Manually update app
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
### Deploy the updated application
```
kubectl get pods
```
### Manually Scale pods
```
kubectl scale --replicas=3 deployment/azure-vote-front
```
To update the application, use the kubectl set command. Update `<acrLoginServer>` with the login server or host name of your container registry, and specify the v2 application version:  
```
kubectl set image deployment azure-vote-front azure-vote-front=<acrLoginServer>/azure-vote-front:v2
```
### Monitor the deployment
```
kubectl get pods
```
### Test the updated application
```
kubectl get service azure-vote-front
```  
--- 
## Part 7 - Upgrade Kubernetes in AKS
### Get available cluster version
```
az aks get-upgrades --resource-group myResourceGroup --name myAKSCluster --output table
```
### Upgrade a cluster
##### Note
You can only upgrade one minor version at a time. For example, you can upgrade from 1.9.11 to 1.10.9, but cannot upgrade from 1.9.6 to 1.11.x directly. To upgrade from 1.9.11 to 1.11.x, first upgrade from 1.9.11 to 1.10.x, then perform another upgrade from 1.10.x to 1.11.x.  
```
az aks upgrade --resource-group myResourceGroup --name myAKSCluster --kubernetes-version 1.10.9
```
This resulted in a conflict.  
### Validate an update
```
az aks show --resource-group myResourceGroup --name myAKSCluster --output table
```
### Delete the cluster - NOT PART OF THE TUTORIAL!!!
```
az group delete --name myResourceGroup --yes --no-wait
```
When you delete the cluster, the Azure Active Directory service principal used by the AKS cluster is not removed. For steps on how to remove the service principal, see AKS service principal considerations and deletion.  
https://docs.microsoft.com/en-us/azure/aks/kubernetes-service-principal#additional-considerations  
---
## Part 8 - Deply SQL Server and PVC in AKS
### Create an SA password
```kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"```  
### Create Storage
```
kind: StorageClass
apiVersion: storage.k8s.io/v1beta1
metadata:
     name: azure-disk
provisioner: kubernetes.io/azure-disk
parameters:
  storageaccounttype: Standard_LRS
  kind: Managed
---
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: mssql-data
  annotations:
    volume.beta.kubernetes.io/storage-class: azure-disk
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 8Gi
```
Save the file (for example, pvc.yaml).  
### Create the persistent volume claim in Kubernetes.  
```kubectl apply -f <Path to pvc.yaml file>```  
### Verify the persistent volume claim.  
```kubectl describe pvc <PersistentVolumeClaim>```
### Metadata about the persistent volume claim
```kubectl describe pvc mssql-data```  
### Verify the persistent volume.  
```kubectl describe pv```  
### Create the deployment
```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssql-deployment
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssql
    spec:
      terminationGracePeriodSeconds: 10
      containers:
      - name: mssql
        image: mcr.microsoft.com/mssql/server:2017-latest
        ports:
        - containerPort: 1433
        env:
        - name: MSSQL_PID
          value: "Developer"
        - name: ACCEPT_EULA
          value: "Y"
        - name: MSSQL_SA_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mssql
              key: SA_PASSWORD 
        volumeMounts:
        - name: mssqldb
          mountPath: /var/opt/mssql
      volumes:
      - name: mssqldb
        persistentVolumeClaim:
          claimName: mssql-data
---
apiVersion: v1
kind: Service
metadata:
  name: mssql-deployment
spec:
  selector:
    app: mssql
  ports:
    - protocol: TCP
      port: 1433
      targetPort: 1433
  type: LoadBalancer
```
Copy the preceding code into a new file, named sqldeployment.yaml.
### Create the deployment.  
```kubectl apply -f <Path to sqldeployment.yaml file>```  
The deployment and service are created. The SQL Server instance is in a container, connected to persistent storage.
### View the status of the pod
```kubectl get pod```.  
### Verify the services are running
```kubectl get services```  
### More information about the status of the objects in the Kubernetes cluster  
```az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>```  




