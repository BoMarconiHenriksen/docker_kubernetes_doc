# Nginx Behind MetalLB in RKE
This was made by Adrian Goins from Rancher. Checkout his video for more information https://www.youtube.com/watch?v=iqVt5mbvlJ0&t=519s  
1. Disable the default Nginx in Rancher the UI.  
2. Run the mandatory command from ingress-nginx docomentary.  
```kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.26.2/deploy/static/mandatory.yaml```  
3. Run the cloud-generic from ingress-nginx Github repository.  
```https://github.com/kubernetes/ingress-nginx/tree/master/deploy/cloud-generic```  
Or run the yaml cloud-generic.yaml file in the cloud-generic folder.  
4. Run the yaml files in the rancher-demo folder.  
