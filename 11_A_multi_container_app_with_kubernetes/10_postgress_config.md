# Postgres Config files
1. Create a file called ```postgres-deployment.yaml```  
2. Add this code.  
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: postgres-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      component: postgres
  template:
    metadata:
      labels:
        component: postgres
    spec:
      containers:
        - name: postgres
          image: postgres
          ports:
            - containerPort: 5432
```
--- 
1. Create a file called ```postgres-cluster-ip-service.yaml```  
2. Add this code.  
```
apiVersion: v1
kind: Service
metadata:
  name: postgres-cluster-ip-service
spec:
  type: ClusterIP
  selector:
    component: postgres
  ports:
    - port: 5432
      targetPort: 5432
```
```kubectl apply -f k8s```  
```kubectl get pods```  
```kubectl get deployments```  
```kubectl get services```  
