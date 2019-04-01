# Express API Deployment Config - multi-server
1. Create a file called ```server-deployment.yaml```  
2. Add this code.  
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: server-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      component: server
  template:
    metadata:
      labels:
        component: server
    spec:
      containers:
        - name: server
          image: bomarconi/multi-server
          ports:
            - containerPort: 5000
```
# Cluster IP for the Express API - multi-server
1. Create a file called ```server-cluster-ip-service.yaml```
2. Add this code.  
```
apiVersion: v1
kind: Service
metadata:
  name: server-cluster-ip-service
spec:
  type: ClusterIP
  selector:
    component: server
  ports:
    - port: 5000
      targetPort: 5000
```
