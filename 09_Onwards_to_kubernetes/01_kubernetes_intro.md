# The Why's and What's of Kubernetes
### What is Kubernetes?
For a better understanding see the basic_cluster.png.  
If we want to scale our application we will only scale those containers that are most busy. With E.B. it will scale the instance with all the containers. The result is that we don't have control over what each container is doing. We are also using more resouces that we need if it's only one container that is busy. With Kubernetes you can have diffrent machines running each container. You then get more control over wahat each container is running.  
#### Cluster in Kubernetes
Contains a master and one or more nodes.
A *node* is a virtual machine or a physical computer that is going to be used to run some number of diffrent containers.  
All the nodes are managed by a *master*. The master has a sets of diffrent programs running on it that controls what each of the nodes are running at a given time.  
As a developer we interact with a Kubernetes cluster by reaching out to the master. We give some directions to the master f.eks. run 5 images of the worker image. The master then reley the command to the nodes.  
Outside of the cluster we have a loadbalancer that will take requests and send them to the nodes.  
> Kubernetes is a system for running many diffrent containers over multiple diffrent machines.  

### Why use Kubernetes?
If you need to scale your application.  
> Use Kubernetes when you need to run many diffrent containers with diffrent images.  
