# Setting up Ingress Locally
The documentation is a little bit confusing so we are going to take it stpe by step https://kubernetes.github.io/ingress-nginx/deploy/  
1. Click Generic Deployment  
> No matter in which cloud you deploy you have to do the mandatory commands.  
```kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/mandatory.yaml```   
2. Copy the mandatory command and run inside your terminal.  
If you want to see whats happening behind the scene. Just copy the link and pate it into your browser to inspect the config file.  
3. Click on minikube on the documentation page.  
4. Copy the "For standard usage" command and past it into the terminal.  
```minikube addons enable ingress```    
5. In the documentation scroll down to GCE-GKE and copy the only the link to see the config file. Here you can see what is going to created on google cloud.  
