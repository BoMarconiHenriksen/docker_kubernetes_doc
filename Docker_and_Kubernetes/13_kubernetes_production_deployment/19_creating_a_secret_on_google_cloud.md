# Creating a Secret on Google Cloud
In the terminal on google cloud you can test the cluster ```kubectl get pods```  
The password in the end does not have to be the same as we made in the developemnt environment.  
```
kubectl create secret generic pgpassword --from-literal PGPASSWORD=password123```  
```
1. Reload the Kubernetes Engine dashboard page and click on configuration.  
2. Check that the secret is created.  
