# Creating an Encoded Secret
This password is related to postgres. Getting access to the database.  
We are going to use the Secret object.  
The purpose with a secret is to store password or other environment variables that you want to protect.  
Most of our environment variables that we have in our config files should be in the secret object.  
> The Secret object stores a piece of information in the cluster, such as a database password.  
We will not use a config file to create the secret object. Instead we are going to run an imperative command.  
We need to be sure, that when we take the app to the production that we create the secret manually as well.  
### Creating a secret
> ```kubectl create secret generic <secret_name> --from-literal key=value```  
*create* - imperative command to create a new object.  
*secret* - type of object we are going to create.  
*generic* - type of secret.  
*secret_name* - name of secret, for later referance in a pod config.  
*--from-literal* we are going to add the secret information into this command, as oppose to from . file.  
*key=value* key-value pair of the secret information.  
```kubectl create secret generic pgpassword --from-literal PGPASSWORD=password123```  
#### See what secrets are created
```kubectl get secrets```  
