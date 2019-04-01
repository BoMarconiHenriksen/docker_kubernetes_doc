# Claim Config File
We are going to wite a persistent volume claim.  
1. cd into the k8s directory.  
2. Create a new file called ```database-persistent-volume-claim.yaml```  
3. Add this code.  
```
apiVersion: v1
# Kubernetes must find an instance of storage that meets the spec requirements
kind: PersistentVolumeClaim
metadata:
  name: database-persistent-volume-claim
spec:
  accessModes:
    # Can be used by a single node
    - ReadWriteOnce
  resources:
    requests:
      # Kubernetes find a storage that has 2gb of space
      storage: 2Gi
```

### Access Mode
We have 3 type of access modes.  
1. ReadWriteOnce --> Can be used by a *single node*.
2. ReadOnlyMany --> *Multiple nodes* can *read* from this.  
3. ReadWriteMany --> Can be *read and written* to by *many nodes*.  
