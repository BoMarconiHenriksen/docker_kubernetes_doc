# Connecting to Running Containers
We have to feed the pod and service files into the Kubernetes cluster with kubectl and try to access the running container.  
#### Feed a config file to kubectl
```kubectl apply -f <filename>```
*apply* change the current configuration of our cluster.  
*-f* specify a file that has the congif changes.  
In the command line run:  
1. cd simplek8s  
2. kubectl apply -f client-pod.yaml  
3. kubectl apply -f client-node-port.yaml  
4. kubectl get pods  
5. kubectl get services  
6. minikube ip  
7. Open your browser and go to: 192.168.10.179:31515  
