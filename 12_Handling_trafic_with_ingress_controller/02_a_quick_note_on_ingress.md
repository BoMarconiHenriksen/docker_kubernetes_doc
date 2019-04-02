# A Quick Note on Ingress
> Ingress exposes a set of services to the outside world.  
The Nginx Ingress is used to route the incoming request to the right pod.  
In Kubernetes there are diffrent way of implementaion of an Ingress.  
For this tutorial we are going to use Nginx Ingress.  
# Important Note otherwise documentation will be confusing!
We are going to use ingress-nginx. a community(a part of the official Kubernetes organisation) led project https://github.com/kubernetes/ingress-nginx  

We are *NOT* using Kubernetes-ingress, a project led by the company nginx https://github.com/nginxinc/kubernetes-ingress  

They are seperate project and work diffrently.  
# One Other Quick Note!
> The setup of ingress-nginx changes depending on your environment(local, GC, AWS, AZURE ect).  
For this tutorial we are going to set up ingress-nginx on local and GC.  
