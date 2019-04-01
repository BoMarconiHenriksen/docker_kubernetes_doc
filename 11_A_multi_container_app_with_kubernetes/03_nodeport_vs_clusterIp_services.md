# NodePort vs ClusterPort Services
We use Services to set up networking for an object in Kubernetes cluster.  
*NodePort* exposes a set of pods to the outside world(only good for development).  
*ClusterIP* exposes a set of pods to other objects in the cluster. It's more restrictic. Nobody outside can access the object that this service it merried up to/pointing to. No access from outside the cluster.  
The traffic from outside will go to the Ingress Service and then it will be routed to the diffrent Services.  
