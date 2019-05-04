# Creating and Applying Redis Config
1. Create a new file called ```redis-deployment.yaml```  
2. Add this code.  
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      component: redis
  template:
    metadata:
      labels:
        component: redis
    spec:
      containers:
        - name: redis
          image: redis
          ports:
          - containerPort: 6379
```
### Create a cluster ip service for redis
1. Create a file called ```redis-cluster-ip-service.yaml```  
2. Add this code.  
```
apiVersion: v1
kind: Service
metadata:
  name: redis--cluster-ip-service
spec:
  type: ClusterIP
  selector:
    component: redis
  ports:
    - port: 6379
      targetPort: 6379
```
```kubectl apply -f k8s```  
```kubectl get pods```  
```kubectl get deployments```  
```kubectl get services```  
