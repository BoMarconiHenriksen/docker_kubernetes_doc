# Recreating the Deployment
1. Delete .travis.yaml, docker-compose.yml and Dockerrun.aws.json  
We are going to rely on Kubernetes so we don't need these files anymore.  
2. Delete the nginx folder. For routing we are going to rely on the Ingress Service.  
3. Create a folder called k8s. Is going to contain all the configuration files for the project.  
### We'll start with multi-client
1. cd into k8s folder.  
2. Create a file called ```client-deployment.yaml```  
3. Add this code.  
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: client-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      component: web
  template:
    metadata:
      labels:
        component: web
    # The containers that runs inside the pod
    spec:
    containers:
      - name:  client
        image: bomarconi/multi-client
        ports:
        # The port is mapped up to the multi-client image
        - containerPort: 3000
```
