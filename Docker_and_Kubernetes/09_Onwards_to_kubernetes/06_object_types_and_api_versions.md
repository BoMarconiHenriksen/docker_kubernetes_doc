# Object Types and API Versions
When we make a config file in Kubernetes we are not creating a container we are making an object.  
Eventually we are going to take to two configuaration files and feed them into the kubectl cli tool.  
When we ass them in kubectl is going to create two objects out of each file.  
An object is a *thing* that exist inside our Kubernetes cluster.  
We are making special kind of objects f.eks. StatefulSet, ReplicaController, Pod or Service.  
These objects have very specific purposes to make the application work the way we expect.  
Some objects is used to run a container like a Pod.  
Some objects is used to monitor a container.
Service is going to set up some kind of networking.  


### kind
Kind indicate the type of object we want to make.  

### apiVersions
Scope or limits the types of objects that we can create in a specification file.  
apiVersion: v1 open up to access to us to a predefined sets of diffrent obejct types.  
Each API version defines a diffrent set of *objects* we can use.  
