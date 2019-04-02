# Load Balancer Services
> LoadBalancer is a legacy way of getting network traffic into a cluster.  
A loadBalncer does two diffrent things inside your cluster.  
You create a loadBalancer with a config file of type Service and a subtype of loadBalancer.  
You then allow access to a specific set of pods inside of your application.  
If you have two pods the loadBalancer would not give us access to both pods.  
When you create a loadBalncer service Kubernetes in the background will reach out to your cloud provider and use their definitions of what a loadBalancer is. It will then configer that resource outside your cluster and send trafic into the cluster and access the loadBalancer service that govern access to a very specific pod.   

> Ingress is the new and better way to get trafic into your cluster.  
