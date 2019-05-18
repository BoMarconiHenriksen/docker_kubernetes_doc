# Get started locally with kubernetes
Starts up a new cluster or start up the old cluster.
```minikube start --vm-driver=hyperv --hyperv-virtual-switch="Primary Virtual Switch" --v=7 --alsologtostderr```  

```minikube status```  

#### Get the ip
```kubectl cluster-info```  
```kubectl get services```  

#### Create a secret for the database
More information https://github.com/BoMarconiHenriksen/docker_tutorial/blob/master/Docker_and_Kubernetes/11_A_multi_container_app_with_kubernetes/20_creating_an_encoded_secret.md
```kubectl create secret generic pgpassword --from-literal PGPASSWORD=password123```  

#### Apply all the files locally. Applys all the files in a folder.
```kubectl apply -f k8s```  

### Remember to set up ingress locally if you have the ingress config file
https://github.com/BoMarconiHenriksen/docker_tutorial/blob/master/Docker_and_Kubernetes/12_Handling_trafic_with_ingress_controller/04_setting_up_ingress_locally.md  

### Test it
minikube ip and go to the ip address in your browser.  
minikube dashboard  
