# Why Use Services?
#### Connect to the local cluster
1. minikube ip  
2. Open the brouser and enter ```<the ip you just got>:31515```  
3. ```kubectl get pods -o wide```  
> Every pod we create gets it's own ip address assign to it. It's internally to our local machine. We can not access it from our machine only through the node. If the pod gets deleted and recreated it can get a new ip address. The service will connect the recreated pod and make it easier for to access it if the ip address change. 
