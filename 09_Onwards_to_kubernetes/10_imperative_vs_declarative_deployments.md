# Imperative vs Declarative Deployments
### Important Takeaways about Kubernetes
1. Kubernetes is a system to deploy containerized apps.  
2. Nodes are individual machines(or VMs) that run containers.  
3. Masters are machines(or VMs) with a set of programs to manage nodes.  
4. Kubernetes didn't build our images - it got them from somewhere else.  
5. Kubernetes(the master) decided where to run each container - each nodescan run a dissimilar set of containers.  
6. To deploy something, we update the desired state of the master with a config file(important).  
7. The master works constantly to meet your desired state(important).  
### Imperativ Deployments
> Do exactly these steps to arrive at this container setup.  
We say create that one, delete that one ect...  
Giving commands.  
You have to figure out the current state and customize your update with that state.  

### Declarativ Deployments
> Our container setup should look like this, make it happen.  
We say to our master we want 4 containers and you figure out how to do that.  
Guidence.  
