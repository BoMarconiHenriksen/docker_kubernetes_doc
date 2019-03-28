# Kubernetes in Development and Production
There is a big diffrence running Kubernetes in development environment and production environment.  
In development we use *minikube* which is a command line tool that purpose is to setup a tiny cluster on your local computer.  
In production we often use managed solutions which are cloud solutions like AWS, Azure Google ect. They will setup the Kubernetes cluster and take care of a lot of low level tasks to make it work.  
It's possible to set it up yourself...  
### Setup process locally
Check the minikube.png  
Minikube creates and runs a Kubernetes cluster on your local machine.  
To interact with the cluster we are going to use a program called kubectl. It's used for managing containers in the node.  
When you go to production the minikube falls away.  
Be aware that kubectl is also used in production.  
This is the plan:  
1. Install Kubectl(cli for interacting with our master).  
2. Install a VM driver(virtualbox - used to make a VM that will be your single node).  
3. Install minikube(runs a single node on that VM).  
