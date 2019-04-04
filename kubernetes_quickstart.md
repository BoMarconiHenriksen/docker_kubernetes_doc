# Get started locally with kubernetes
Starts up a new cluster or start up the old cluster.
```minikube start --vm-driver=hyperv --hyperv-virtual-switch="Primary Virtual Switch" --v=7 --alsologtostderr```  

```minikube status```  

#### Get the ip
```kubectl cluster-info```  
```kubectl get services```  

#### Create a secret for the database
More information https://github.com/BoMarconiHenriksen/docker_tutorial/blob/master/11_A_multi_container_app_with_kubernetes/20_creating_an_encoded_secret.md  
```kubectl create secret generic pgpassword --from-literal PGPASSWORD=password123```  

#### Apply all the files locally. Applys all the files in a folder.
```kubectl apply -f k8s```  
