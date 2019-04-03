# Configuring the GCloud CLI on Cloud Console
1. Go to Kubernetes Engine on google cloud.  
2. We have to manually make the PGPASSWORD secret on google cloud. Like we did in the server-deployment.tml file  
3. On the right handside in the top click activate cloud shell.  
> We also need to set our project id, our compute zone and all credientials...  
4. ```gcloud config set project learned-alcove-236015``` - The last part is the project id.  
5. ```gcloud config set compute/zone europe-north1-a```  
6. ```gcloud container clusters get-credentials multi-cluster```  
> You only have to run these commands one time unless you create a new project or a new cluster. It's the same files you have to run as you have written in the .travis.yml file.  
