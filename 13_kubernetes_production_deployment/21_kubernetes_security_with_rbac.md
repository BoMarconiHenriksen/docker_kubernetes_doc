# Kubernetes Security with RBAC
Role Based Access Control.  
1. Limits who can access and modify objects in our cluster.  
2. Enable on Google Cloud by default.  
3. Tiller wants to make changes to our cluster, so it needs to get some permissions set.  
In a production environment we want to log things down and make sure that useres or programs do not have the ability to change the configuration of the cluster.  
> So RBAC have the ability to limit who can do what inside our cluster.  
*User Accounts* - Identifies a *person* administering our cluster.  
*Service Accounts* - Identifies a *pod or a program/process* administering a cluster.  
*ClusterRoleBinding* - Authorizes an account to do a certain set of actions acreoss the entire cluster.  
*RoleBinding* - Authorizes an account to do a certain set of actions in a *single namespace*.  
*namespace* - You can isolate diffrent resources into diffrent namespaces.  
