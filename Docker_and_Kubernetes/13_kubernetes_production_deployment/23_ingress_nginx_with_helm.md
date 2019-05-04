# Ingress-Nginx with Helm
https://kubernetes.github.io/ingress-nginx/deploy/#using-helm  
We have RBAC enabled so we have to write this command.  
```helm install stable/nginx-ingress --name my-nginx --set rbac.create=true```  
### The Result of Ingress-Nginx
Refresh Kubernetes Engine dashboard.  
Click workloads.  
*my-nginx-nginx-ingress-controller* is the Deployment that manages the pod that runs the controller thats going to read our ingress config file and set up nginx.  
*default-backend* has some health checks inside of it.  
##### Click the services tab.  
Be sure that for the load balancer that there are 2 endpoints.  
##### On the navigation menu click on network services.  
This is the google cloud loadBalancer that was created for us.  
Here you can see how to connect to the load balancer and you can see what ip address the load balancer can reach(diffrent nodes).  
