# Creating the Ingress Config
To recap our routing ruleset is...  
1. The request that has a path of / is going to the client.  
2. The request that has a path of /api is going to the server.  
---
1. cd into the k8s directory and create a file called ```ingress-service.yaml```.  
2. Add this code.  
```
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: ingress-service
  # annotations is additional options. Higher level configuration around the Ingress object
  annotations:
    # Tells Kubernetes we want to create a nginx controller based on the nginx project
    kubernetes.io/ingress.class: nginx
    # Configure how our copy of nginx behaves
    # This behaivor removes the /api from the incomming requests so we dont have to write /api on the server
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
    - http:
			paths:
			- path: /
				backend:
					serviceName: client-cluster-ip-service
					servicePort: 3000
			- path: /api/
				backend:
					serviceName: server-cluster-ip-service
					servicePort: 5000
```
3. ```kubectl apply -f k8s```  
