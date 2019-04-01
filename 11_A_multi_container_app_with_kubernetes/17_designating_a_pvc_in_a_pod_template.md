# Designating a PVC in a Pod Template
1. Open the postgres-deployment.yaml file.  
2. We are going to update the template section.  
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
      # Sets up the request on the pod to reach out to kubernetes saying I need some types of long term storage
      volumes:
        - name: postgres-storage
          persistentVolumeClaim:
            # From the database-persistent-volume-claim.yaml
            claimName: database-persistent-volume-claim
      containers:
        - name: postgres
          image: postgres
          ports:
            - containerPort: 5432
          # Here is how I want to use it(pvc) inside my container
          volumeMounts:
              # Volumes has to be identical with volumeMounts
            - name: postgres-storage
              # Where inside the container should the storage be made availble
              # This will actually be stored inside the volumes. Has to be default storage path for the db
              mountPath: /var/lib/postgresql/data
              # This is only for postgres. Any data that is stored inside the mountPath is stored in a folder called postgres inside the PVC
              subPath: postgres
```
