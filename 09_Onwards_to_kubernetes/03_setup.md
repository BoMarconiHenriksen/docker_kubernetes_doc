# Setup on windows
https://www.c-sharpcorner.com/article/getting-started-with-kubernetes-on-windows-10-using-hyperv-and-minikube/  

#### Install goggle cloud sdk for windows.  
https://cloud.google.com/sdk/docs/quickstart-windows  

Run gcloud as administrator  
gcloud components install kubectl  

#### Download minikube 
Open powerShell as administrator.   
https://github.com/kubernetes/minikube/releases  
change the name to minikube.exe  

Now, keep it at any location as per your wish.  
Now add this folder path as part of your PATH environment variable.  
Open 'System Properties' by searching 'View advanced system settings' in your machine and update the PATH variable.  
Open powerShell or cmd and test that minikube works: ```minikube version```  
Run minikube commands from powerShell.  

#### Install minikube on Hyper-V
Follow this tutorial.  
https://docs.docker.com/machine/drivers/hyper-v/#2-set-up-a-new-external-network-switch-optional  

minikube start --vm-driver=hyperv --hyperv-virtual-switch="Primary Virtual Switch" --v=7 --alsologtostderr  
(you can add a memory flag: --memory 4096)  

minikube status  
minikube delete  
