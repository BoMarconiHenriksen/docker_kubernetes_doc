# Running Containers in Pods
### Pod
We refer to a virtual machine as a node.  
That node is being used to run some number of diffrent objects.  
One of the basic object we are going to use is called a pod.  
A Pod is a grouping of containers with a common purpose.  
In Kubernetes there are no such thing as just creating a container on a cluster. We can't run a single container by itselves with no accotiated overhead. The smallest thing we can deploy is a Pod. So we are always going to create a container inside a Pod.  
#### Why make a Pod?
*See pod_example.png  
The requirment of a Pod is to run one or more containers inside of it.  
The purpose of a Pod is to allow to grouping containers with a very similar purpose.  
We are grouping containers that have a very thight coupled relationsship so containers that must be executed with eachother.  

> You can use the name in the spec: containers to networking between containers that is running inside a single Pod.  

ports --> we want to expose port 3000(we sat up that nginx listen to port 3000) to the outside world. We also need to set up a target port in the Service object.  
