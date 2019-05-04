# Behind the Scenes of Ingress
We have been writeing config files describing the desired state.  
We feed to kubectl that creates a deployment object(deployment is a type of *controller*).  
It's up to the deployment object to look at the curent state and the desired state and it will then figure out a way to get from the current state to the desired state. Eventually it will create the pods(this is our new state).  
In Kubernetes a controller is any type of object that constantly works to make some desired state.  
#### It's the same strategy for Ingress.  
We are going to create Ingress routing rules in a config file to get trafic to services(desired state).  
We then fedd that config file into kubectl.  
Kubectl creates an ingress controller thats going to look at our current state and desired state and then create some infrastructure that is going to make our desired state a reality.  
The ingress controller will constantly works to make sure these routing rules are setup.  
The controller is going to create a pod running Nginx thats going to have a set of rules to make sure trafic comes in and send to the services inside our cluster.  
> We are going to create an ingress config file with a set of routing rules and then feed it to kubectl.  
For Kubernetes ingress nginx the ingress controller and the thing that accepts trafic and routes it of to the right location is the same thing.  
!(ingress)[ingress.png]  
### More Behind the Scenes of Ingress
Google Cloud will create a Google Cloud Load Balancer for us. It's a cloud native load balancer https://cloud.google.com/load-balancing/. This will get trafic into our cluster. The Deployment with nginx-controller/nginx-pod will get a LoadBalncer Service attached to it.  
By default there will be another Deployment sest up inside the cluster called a default-backend pod.  
It's used for a series of health checks to make sure your cluster is working the it's supposed to.  
In the real world you would replace the express backend with the default-backend.  
!(ingress_on_google_cloud)[ingress_on_google_cloud.png]  
#### Why not use a Load Balancer Service with a custom Nginx?
When you make use of the nginx-ingress project it's actually has code add into it that is aware of that it run inside a Kubernetes cluster an example of this is:
We use ClusterIp Service infront of a Deployment. With nginx-ingress the routing will bypass the ClusterIP service. This is done to because of sticky sessions(if one user sends 2 requests it goes to the same container). The ClusterIp is still used to monotering the Deployment.  
For more on kubernetes ingres https://www.joyfulbikeshedding.com/blog/2018-03-26-studying-the-kubernetes-ingress-system.html  
