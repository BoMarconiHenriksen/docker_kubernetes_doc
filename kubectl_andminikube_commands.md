# Kubectl and minikube commands
### Kubectl
#### Add an object to  cluster
> ```kubectl apply -f <filename>```  
```kubectl apply -f client-pod.yaml```  
#### Apply all the files in a folder
> ```kubectl apply -f <folder name>```  
```kubectl apply -f k8s```
#### Update an object and inspect the changes
> apply is how we make any changes to our kubernetes cluster.  
> describe is used to print out information about the object.  
> ```kubectl describe <object type> <object name>```  
```kubectl apply -f client-pod.yaml```  
```kubectl describe pod client-pod```  
#### Show the pods that are running
```kubectl get pods```  
#### Remove an object that is running
> delete a running object.  
```kubectl delete -f <config file or path to config file>```  
```kubectl delete -f client-pod.yaml```  
#### Get the status of deployments.  
```kubectl get deployments```  
#### Get the ip of a pod locally and additional information
```kubectl get pods -o wide```  
#### Error when deploying pod
```kubectl describe <name og pod>```
#### Imperative Updating of Deployment's image
> ```kubectl set image <object_type> / <obejct_name> <container_name> = <new_image_to_use>``` (is done in the folder where your client-deployment.yaml file is)  
docker build -t bomarconi/multi-client:v5 .  
docker push bomarconi/multi-client:5  
```kubectl set image deployment/client-deployment client=bomarconi/multi-client:5```  
kubectl get pods  
#### Entering docker in the virtual machine which is diffrent from the docker on your machine
```eval $(minikube docker-env)``` # Only works for that terminal.  
#### Delete a deployment locally
```kubectl delete deployment client-deployment```
#### Get persistent volume  
```kubectl get pv```  
#### Get all the claims
```kubectl get pvc```  
#### Creating a secret
> ```kubectl create secret generic <secret_name> --from-literal key=value```  
```kubectl create secret generic pgpassword --from-literal PGPASSWORD=password123```  
#### See what secrets are created
```kubectl get secrets```  



# minikube Commands
#### Get the local cluster ip
minikube ip  
#### Connect to the local cluster
1. minikube ip  
2. ```<the ip you just got>:31515```  
#### Delete a lucal cluster
```minikube delete```  
