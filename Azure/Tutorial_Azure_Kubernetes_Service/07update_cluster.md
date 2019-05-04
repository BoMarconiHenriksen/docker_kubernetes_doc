# Upgrade Kubernetes in Azure Kubernetes Service
As part of the application and cluster lifecycle, you may wish to upgrade to the latest available version of Kubernetes and use new features. An Azure Kubernetes Service (AKS) cluster can be upgraded using the Azure CLI.  

In this tutorial, part seven of seven, a Kubernetes cluster is upgraded. You learn how to:  

Identify current and available Kubernetes versions  
Upgrade the Kubernetes nodes  
Validate a successful upgrade  
### Get available cluster version
Before you upgrade a cluster, use the az aks get-upgrades command to check which Kubernetes releases are available for upgrade:  
```
az aks get-upgrades --resource-group myResourceGroup --name myAKSCluster --output table
```
### Upgrade a cluster
To minimize disruption to running applications, AKS nodes are carefully cordoned and drained. In this process, the following steps are performed:  

1. The Kubernetes scheduler prevents additional pods being scheduled on a node that is to be upgraded.  
2. Running pods on the node are scheduled on other nodes in the cluster.  
3. A node is created that runs the latest Kubernetes components.  
4. When the new node is ready and joined to the cluster, the Kubernetes scheduler begins to run pods on it.  
5. The old node is deleted, and the next node in the cluster begins the cordon and drain process.  
6. Use the az aks upgrade command to upgrade the AKS cluster. The following example upgrades the cluster to Kubernetes version 1.10.9.  

##### Note
You can only upgrade one minor version at a time. For example, you can upgrade from 1.9.11 to 1.10.9, but cannot upgrade from 1.9.6 to 1.11.x directly. To upgrade from 1.9.11 to 1.11.x, first upgrade from 1.9.11 to 1.10.x, then perform another upgrade from 1.10.x to 1.11.x.  
```
az aks upgrade --resource-group myResourceGroup --name myAKSCluster --kubernetes-version 1.10.9
```
This resulted in a conflict.  
### Validate an update
Confirm that the upgrade was successful using the az aks show command as follows:  
```
az aks show --resource-group myResourceGroup --name myAKSCluster --output table
```
### Delete the cluster
As this tutorial is the last part of the series, you may want to delete the AKS cluster. As the Kubernetes nodes run on Azure virtual machines (VMs), they continue to incur charges even if you don't use the cluster. Use the az group delete command to remove the resource group, container service, and all related resources.  
```
az group delete --name myResourceGroup --yes --no-wait
```
When you delete the cluster, the Azure Active Directory service principal used by the AKS cluster is not removed. For steps on how to remove the service principal, see AKS service principal considerations and deletion.  
https://docs.microsoft.com/en-us/azure/aks/kubernetes-service-principal#additional-considerations  

### AKS overview
https://docs.microsoft.com/en-us/azure/aks/intro-kubernetes  
