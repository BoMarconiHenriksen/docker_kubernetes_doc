# Assigning Tiller a Service Account
Open the google cloud shell on the Kubernetes Engine dashboard.  
Enter the 2 commands.  
> Create a new service account called tiller in the kube-system namespace.  
```kubectl create serviceaccount --namespace kube-system tiller```  
> Create a new clusterRoleBinding with the role 'cluster-admin' and assign it to service account 'tiller'  
```kubectl create clusterrolebinding tiller-cluster-role --clusterrole=cluster-admin --serviceaccount=kube-system:tiller```  
#### Initialize Helm
We need to tell Helm what service account Helm should be assigned.  
--upgrade = latest version of helm.  
```helm init --service-account tiller --upgrade```  
