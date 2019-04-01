# ClusterIP for multi-client
1. cd into k8s folder.  
2. Create a new file called ```client-cluster-ip-service.yaml```  
3. Add this code.  
```
apiVersion: v1
kind: Service
metadata:
  name: client-cluster-ip-service
# Configure the way this service behave
spec:
  type: ClusterIP
  # What pods is it going to provide access to. Reference to client-deployment.yaml label: component: web
  selector:
    component: web
  ports:
    - port: 3000 # Other pods that needs access to the multi-client pod through the ClusterIP Service
      targetPort: 3000 # The port on the target pod(multi-client) that we provide access to
```
