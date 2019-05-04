# Triggering Deployment Update
This is a challing step and there are not any good solutions arounf it.  
Take a look at this discussion https://github.com/kubernetes/kubernetes/issues/33664  
### Why is it so challaning
To make an update you change the template and do an apply. In the config file we don't have anything that say we want to use a specific version of our image. So when we update our image on docker hub we don't have anything in the config file that say use the latest image. The problem is if there is no changes to the configuration file and apply it with kubectl then kubectl will reject the file.  
To check this write.  
```kubectl apply -f client-deployment.yaml``` --> it's going to tell us the file is unchanged.  
#### We have 3 options to make the change
1. Manually delete pods to get the deployment to recreate them with the latest version --> seems silly.  
2. Tag build images with a real version number and specify that version in the config file --> adds an extra step in the deployment process.  
3. Use an imperative command to update the image version the deployment should use --> using an imperativ command. Outconfig file will not be uptodate with the right version tag.  
> We are going to use option 3 in the next section.  
