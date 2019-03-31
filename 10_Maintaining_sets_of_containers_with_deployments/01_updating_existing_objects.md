# Updating Existing Objects
We want to update theexisting pod to use the multi-worker image.  
### Imperativ Approch
Run a command to list out current running pods --> Run a command to update the current pod to use  new image.  
### Declarativ Approch
Update our config file that originally created the pos --> Throw the update config file into kubectl.  
If there is a container with identical name and type(kind) then it will take the updated config file and apply it to the object that already exist inside the cluster.  
> So when you update an object the name and kind always has to be the same.  
1. Open the client-pod.yaml file  
2. Change the image to ```image: bomarconi/multi-worker```  
3. kubectl apply -f client-pod.yaml  
4. kubectl get pods  
> apply is how we make any changes to our kubernetes cluster.  
#### inspect a pod so we can check that it changed
describe is used to print out information about the object.  
```kubectl describe pod client-pod```  
