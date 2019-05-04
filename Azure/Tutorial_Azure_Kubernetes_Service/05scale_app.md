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
Kubernetes supports horizontal pod autoscaling to adjust the number of pods in a deployment depending on CPU utilization or other select metrics. The Metrics Server is used to provide resource utilization to Kubernetes, and is automatically deployed in AKS clusters versions 1.10 and higher. To see the version of your AKS cluster, use the az aks show command, as shown in the following example:  
```
az aks show --resource-group myResourceGroup --name myAKSCluster --query kubernetesVersion
```
To use the autoscaler, your pods must have CPU requests and limits defined. In the azure-vote-front deployment, the front-end container already requests 0.25 CPU, with a limit of 0.5 CPU. These resource requests and limits are defined as shown in the following example snippet:  
```
resources:
  requests:
     cpu: 250m
  limits:
     cpu: 500m
```
The following example uses the kubectl autoscale command to autoscale the number of pods in the azure-vote-front deployment. If CPU utilization exceeds 50%, the autoscaler increases the pods up to a maximum of 10 instances. A minimum of 3 instances is then defined for the deployment:  
```
kubectl autoscale deployment azure-vote-front --cpu-percent=50 --min=3 --max=10
```
To see the status of the autoscaler, use the kubectl get hpa command as follows:  
```
kubectl get hpa
```
After a few minutes, with minimal load on the Azure Vote app, the number of pod replicas decreases automatically to three. You can use kubectl get pods again to see the unneeded pods being removed.  
### Manually scale AKS nodes
If you created your Kubernetes cluster using the commands in the previous tutorial, it has one node. You can adjust the number of nodes manually if you plan more or fewer container workloads on your cluster.

The following example increases the number of nodes to three in the Kubernetes cluster named myAKSCluster. The command takes a couple of minutes to complete.  
```
az aks scale --resource-group myResourceGroup --name myAKSCluster --node-count 3
```
