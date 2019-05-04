# Adding Configuration files
Check on docker hub that you have the client image.  
Create a new project folder called ```simplek8s```.  
1. In the root of the new project create a new file called: ```client-pod.yaml```  
2. Add this code.  
```
apiVersion: v1
kind: pod
metadata:
  name: client-pod
  labels:
    component: web
spec:
  containers:
    - name: client
      image: bomarconi/multi-client
      ports:
        - containerPort: 3000
```
3. Create a new file called ```client-node-port.yaml```  
4. Add this code to the file:  
```
apiVersion: v1
kind: Service
metadata:
  name: client-node-port
spec:
  type: NodePort
  ports:
    - port: 3050 # or is it ports?
      targetPort: 3000
      nodePort: 31515
  selector:
    component: web
```
