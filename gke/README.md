# GKE
### Using Cloud Shell to access a private cluster
https://cloud.google.com/kubernetes-engine/docs/how-to/private-clusters  
1. Find your external IP adress by opening the shell in the top right corner.  
```dig +short myip.opendns.com @resolver1.opendns.com```  
2. find cidre blocks in masterAuthorizedNetworksConfig.cidrBlocks[].  
gcloud container clusters describe [cluster name]  
3. Update the cluster.  
```
gcloud container clusters update [cluster name] \  
    --zone [cluster zone] \  
    --enable-master-authorized-networks \  
    --master-authorized-networks [cidre block],[external ip]/32
```  
Example.  
```
gcloud container clusters update k8s-cluster-development \  
    --zone us-central1-c \  
    --enable-master-authorized-networks \  
    --master-authorized-networks 3.1.9.0/24,32.144.119.250/32  
```

3. Get credentials  
```  
gcloud container clusters get-credentials [cluster name] \
    --zone [cluster zone] \
    --project [cluster project]
```  
Example.  
```  
gcloud container clusters get-credentials k8s-cluster-development \
    --zone us-central1-c \
    --project my-k8s-project
```  
### Setup the cloud shell if you don't have a private cluster
1. Log into console.cloud.google.com  
2. Open the shell in the right top corner.  
3. Click the project in the top menu and copy ID.  
```gcloud config set project [add project-id]```
```gcloud container clusters describe c3ng-production [add same zone as cluster]```  
```gcloud container clusters get-credentials [cluster name]```  
### Install Google Cloud SDK Local  
https://cloud.google.com/sdk/docs/downloads-interactive  
### Configuring default settings for the gcloud tool  
#### Add project id
1. Log into console.cloud.google.com  
2. Click the project in the top menu and copy ID.  
```gcloud config set project [add project-id]```
#### Setting a default compute zone
https://cloud.google.com/compute/docs/regions-zones/  
```gcloud config set compute/zone europe-west3-a```  

