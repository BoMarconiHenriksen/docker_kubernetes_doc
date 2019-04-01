# Kubernetes Volumes
##### Volume in Docker
> Some type of mechanism that allows a container to access a filesystem outside itself.  
##### "Volume" in Kubernetes
> An *object* that allows a container to store data at the pod level. So we can write a config file called.  
To persist data in Kubernetes we want to use Persistent Volum Claim or Persistent Volume. We don't want to use Volume.  
#### Volume Object Type
When we create a volume we create datastorage that is tiged to a very specific pod. It's inside the pod.  
The volume is thiged to the pod so if the pod dies the volume will also die. So a volume in Kubernetes will survie a container restart but if the pod gets recreated the volume will die.    
