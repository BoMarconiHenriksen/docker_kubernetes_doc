# Multiple docker installations
The Docker program is connect to docker server. When you have a cluster with a node there is a versoin of docker and also docer server. To connect to that server you can write:  
```eval $(minikube docker-env)``` # Only works for that terminal.  
### Why do this?
1. Use all the same debugging techniques we learned with docker cli(many of these commands are availble through kubectl).  
2. Manually kill containers to test Kubernetes ability to self-heal.  
3. Delete cached images in the node.  



