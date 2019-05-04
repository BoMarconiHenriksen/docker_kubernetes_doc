# Running Containers with Deployments
In a pod there are fields we are not allowed to update.  
Instead of pod we can use deployment.  
> Deployment maintains a set of identical pods, ensuring that they have the correct config and that the right number exists.  
### Pods
1. Runs a single set of containers.  
2. Good for one-off dev purposes.  
3. Rarely used directly in production.  
### Deployment
1. Runs a sest of identical pods(one or more).  
2. Monitors the state of each pod, updating as necessary.  
3. Good for dev.  
4. God for production.  
> Deployment contains a pod template which is a little blog of configuration that says what a pod should look like.  
