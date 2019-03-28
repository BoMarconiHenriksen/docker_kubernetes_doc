# Connecting to Running Containers
We have to feed the pod and service files into the Kubernetes cluster with kubectl and try to access the running container.  
#### Fedd a config file to kubectl
```kubectl apply -f <filename>```
*apply* change the current configuration of our cluster.  
*-f* specify a file that has the congif changes.  
In the command line run:  
1. cd simplek8s  
2. kubectl apply -f client-pod.yaml  
3. 
