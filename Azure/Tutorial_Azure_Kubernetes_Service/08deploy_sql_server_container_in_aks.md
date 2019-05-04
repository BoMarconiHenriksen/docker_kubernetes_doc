# Deploy a SQL Server container in Kubernetes with Azure Kubernetes Services (AKS)
https://docs.microsoft.com/lb-lu/sql/linux/tutorial-sql-server-containers-kubernetes?view=sql-server-ver15  
Learn how to configure a SQL Server instance on Kubernetes in Azure Kubernetes Service (AKS), with persistent storage for high availability (HA). The solution provides resiliency. If the SQL Server instance fails, Kubernetes automatically re-creates it in a new pod. Kubernetes also provides resiliency against a node failure.  
### HA solution on Kubernetes running in Azure Kubernetes Service
You can create and manage your SQL Server instances natively in Kubernetes. The example in this article shows how to create a deployment to achieve a high availability configuration similar to a shared disk failover cluster instance. In this configuration, Kubernetes plays the role of the cluster orchestrator. When a SQL Server instance in a container fails, the orchestrator bootstraps another instance of the container that attaches to the same persistent storage.  

![GitHub Logo](https://github.com/BoMarconiHenriksen/azure-voting-app-redis/blob/master/images/kubernetes-sql.png)  

In the preceding diagram, mssql-server is a container in a pod. Kubernetes orchestrates the resources in the cluster. A replica set ensures that the pod is automatically recovered after a node failure. Applications connect to the service. In this case, the service represents a load balancer that hosts an IP address that stays the same after failure of the mssql-server.  

In the following diagram, the mssql-server container has failed. As the orchestrator, Kubernetes guarantees the correct count of healthy instances in the replica set, and starts a new container according to the configuration. The orchestrator starts a new pod on the same node, and mssql-server reconnects to the same persistent storage. The service connects to the re-created mssql-server.  

![GitHub Logo](https://github.com/BoMarconiHenriksen/azure-voting-app-redis/blob/master/images/kubernetes-sql-after-pod-fail.png)  

In the following diagram, the node hosting the mssql-server container has failed. The orchestrator starts the new pod on a different node, and mssql-server reconnects to the same persistent storage. The service connects to the re-created mssql-server.  

![GitHub Logo](https://github.com/BoMarconiHenriksen/azure-voting-app-redis/blob/master/images/kubernetes-sql-after-node-fail.png)  

### Create an SA password
Create an SA password in the Kubernetes cluster. Kubernetes can manage sensitive configuration information, like passwords as secrets.  
The following command creates a password for the SA account:  
```kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"```  
Replace MyC0m9l&xP@ssw0rd with a complex password.  
To create a secret in Kubernetes named mssql that holds the value MyC0m9l&xP@ssw0rd for the SA_PASSWORD, run the command.  
### Create Storage
Configure a persistent volume and persistent volume claim in the Kubernetes cluster. Complete the following steps:  

1. Create a manifest to define the storage class and the persistent volume claim. The manifest specifies the storage provisioner, parameters, and reclaim policy. The Kubernetes cluster uses this manifest to create the persistent storage.  

The following yaml example defines a storage class and persistent volume claim. The storage class provisioner is azure-disk, because this Kubernetes cluster is in Azure. The storage account type is Standard_LRS. The persistent volume claim is named mssql-data. The persistent volume claim metadata includes an annotation connecting it back to the storage class.  
```
kind: StorageClass
apiVersion: storage.k8s.io/v1beta1
metadata:
     name: azure-disk
provisioner: kubernetes.io/azure-disk
parameters:
  storageaccounttype: Standard_LRS
  kind: Managed
---
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: mssql-data
  annotations:
    volume.beta.kubernetes.io/storage-class: azure-disk
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 8Gi
```
Save the file (for example, pvc.yaml).  
2. Create the persistent volume claim in Kubernetes.  
```kubectl apply -f <Path to pvc.yaml file>```  
<Path to pvc.yaml file> is the location where you saved the file.  
The persistent volume is automatically created as an Azure storage account, and bound to the persistent volume claim.  
3. Verify the persistent volume claim.  
```kubectl describe pvc <PersistentVolumeClaim>```
<PersistentVolumeClaim> is the name of the persistent volume claim.  
In the preceding step, the persistent volume claim is named mssql-data. To see the metadata about the persistent volume claim, run the following command:  
```kubectl describe pvc mssql-data```  
The returned metadata includes a value called Volume. This value maps to the name of the blob.  
4. Verify the persistent volume.  
```kubectl describe pv```  
kubectl returns metadata about the persistent volume that was automatically created and bound to the persistent volume claim.  
### Create the deployment
In this example, the container hosting the SQL Server instance is described as a Kubernetes deployment object. The deployment creates a replica set. The replica set creates the pod.  

In this step, create a manifest to describe the container based on the SQL Server mssql-server-linux Docker image. The manifest references the mssql-server persistent volume claim, and the mssql secret that you already applied to the Kubernetes cluster. The manifest also describes a service. This service is a load balancer. The load balancer guarantees that the IP address persists after SQL Server instance is recovered.  

1. Create a manifest (a YAML file) to describe the deployment. The following example describes a deployment, including a container based on the SQL Server container image.  
```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssql-deployment
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssql
    spec:
      terminationGracePeriodSeconds: 10
      containers:
      - name: mssql
        image: mcr.microsoft.com/mssql/server:2017-latest
        ports:
        - containerPort: 1433
        env:
        - name: MSSQL_PID
          value: "Developer"
        - name: ACCEPT_EULA
          value: "Y"
        - name: MSSQL_SA_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mssql
              key: SA_PASSWORD 
        volumeMounts:
        - name: mssqldb
          mountPath: /var/opt/mssql
      volumes:
      - name: mssqldb
        persistentVolumeClaim:
          claimName: mssql-data
---
apiVersion: v1
kind: Service
metadata:
  name: mssql-deployment
spec:
  selector:
    app: mssql
  ports:
    - protocol: TCP
      port: 1433
      targetPort: 1433
  type: LoadBalancer
```
Copy the preceding code into a new file, named sqldeployment.yaml. Update the following values:  

MSSQL_PID value: "Developer": Sets the container to run SQL Server Developer edition. Developer edition is not licensed for production data. If the deployment is for production use, set the appropriate edition (Enterprise, Standard, or Express).  

persistentVolumeClaim: This value requires an entry for claimName: that maps to the name used for the persistent volume claim. This tutorial uses mssql-data.  

name: SA_PASSWORD: Configures the container image to set the SA password, as defined in this section.  
```
valueFrom:
  secretKeyRef:
    name: mssql
    key: SA_PASSWORD 
```
When Kubernetes deploys the container, it refers to the secret named mssql to get the value for the password.  
Save the file (for example, sqldeployment.yaml).  
2. Create the deployment.  
```kubectl apply -f <Path to sqldeployment.yaml file>```  
```<Path to sqldeployment.yaml file>``` is the location where you saved the file.  
The deployment and service are created. The SQL Server instance is in a container, connected to persistent storage.
To view the status of the pod, type ```kubectl get pod```.  
3. Verify the services are running. Run the following command:  
```kubectl get services```  
For more information about the status of the objects in the Kubernetes cluster, run:  
```az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>```  
