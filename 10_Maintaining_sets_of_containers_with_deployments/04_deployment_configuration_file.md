# Deployment Configuration Files
1. Go to the root project directory and create a new file called ```client-deployment.yaml```  
2. Add this code to the file.  
```
apiVersion: apps/v1
kind: Deployment 
metadata:
  name: client-deployment 
spec:
  replicas: 1
  selector:
    matchLabels:
      component: web
    template:
      metadata:
        labels:
          component: web
      spec:
        containers:
          - name: client 
            image: bomarconi/multi-client
            ports:
              - containerPort: 3000
```
#### template
template contains the configuration for every single pod that is created by this deployment.  
> So every pod that is created and maintained by this deployment is created with the specs that is written in template.  
#### replicas
This is the number of diffrent pods this deployment is supposed to make. We are saying create one pod using the template.  
#### selector
When a deployment create a pod it dos not create the pod directly itselvs and maintain it.  
Instead it reaches out to the Kubernetes API on the master and says *hey master I need you to create a pod and here is the configuration for it*. The master then creates the pod. When the object is created deployment will look for it with what is specified in the component web. So it gives a handle to the label in the template.  
