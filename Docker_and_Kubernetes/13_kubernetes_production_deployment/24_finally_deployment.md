# Finally Deployment!
> Make sure the line breaks are set to LF!!!
Go to your terminal for your local project.  
```git status```  
```git add .```  
```git commit -m " Added deployment scripts."```  
```git push origin master```  
Go to your project at travis.  
Check the tags on docker hub.  
Check the workloads tab in google console.  
##### Check services
The * and /api/ endpoints are the routes you set up in ingress-service.yaml file.  
The ingress-controller is making changes to nginx and hosting nginx at the same time.  
If you click on the ip address you go to the homepage.  
##### Click configuration
service account created by tiller.  
##### Click storage
Here you can see the storage we created.  
