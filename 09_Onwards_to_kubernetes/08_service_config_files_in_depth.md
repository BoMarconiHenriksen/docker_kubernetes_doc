# Service Config Files in Depth
### metadata
Name the Pod that is being created. Mostly used for logging nd we'll see it in the termal when using kubectl.  


### Services
Sets up networking in a Kubernetes Cluster.  
Services have 4 subtypes.  
1. ClusterIp.  
2. NodePort(Exposes a container to the outside world - only good for dev purposes).  
3. LoadBalancer.  
4. Ingress.  
We are making a *NodePort Service* in the ```clien-node-port.yaml``` file.  
The purpose is to expose a container to the outside world(access it from a browser).Normally it's not used in production.  
#### NodePort
See NodePort_Service.png  
The NodePort Service is setting up a cummunication node between the outside world and the Pod.  
Every single node that we create has a program on it called kube-proxy. It's the one single window to the outside world. A request will go to the kube-proxy that will decide where to send the request inside the node.  
The NodePort Service will then forward the request to port 3000 in the container.  
#### Selector and components 
*See NodePort_Service_deep_dive.png*
Insted of naming system Kubernetes uses the label selector system. 
selector: component: web --> This is used as a *name reference* between Pod and a Service. Thats how the two objects are linked together. Looks after a key/value pair: component/web.  
> Is linked togethre with: selector in service and the labels in the Pod.  
You can use another name than component.  
#### ports
See NodePort_Service_ports.png  
Describe all the ports that needs to be open up or mapped on the target object.  
The targetPort is identical to the containerPort in the client-pod.taml.  
*port* is the port that another Pod or another container inside our application could access in order to get access to the multi-client Pod.  
*targetPort* is the port inside the multi-docker pod that we wants to open up trafic to.  
*nodePort* is the port we are going to use to access via a browser. Always has to be a number between 30000 and 32767. This is not used in production because of the high number in the port mappings.  
