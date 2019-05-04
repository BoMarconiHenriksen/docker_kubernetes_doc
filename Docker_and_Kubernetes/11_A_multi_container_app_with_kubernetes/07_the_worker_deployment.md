# The Worker Deployment
1. Create a new file called ```worker-deployment.yaml```  
2. Add this code.  
```
apiVersion: apps/v1
kind: deployment
metadata:
  name: worker-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      component: worker
  template:
    metadata:
      labels:
        component: worker
    spec:
      containers:
        - name: worker
          image: bomarconi/multi-worker
```
