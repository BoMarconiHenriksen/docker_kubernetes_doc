# Setup on windows
https://www.c-sharpcorner.com/article/getting-started-with-kubernetes-on-windows-10-using-hyperv-and-minikube/  

#### Install minikube on Hyper-V
Follow this tutorial.  
https://docs.docker.com/machine/drivers/hyper-v/#2-set-up-a-new-external-network-switch-optional  

After the restart run this command. Be sure to change ```--hyperv-virtual-switch="Primary Virtual Switch"``` if you gave the switch another name.  

minikube start --vm-driver=hyperv --hyperv-virtual-switch="Primary Virtual Switch" --v=7 --alsologtostderr  
(you can add a memory flag: --memory 4096)  

minikube status  
minikube delete 

#### Install goggle cloud sdk for windows.  
https://cloud.google.com/sdk/docs/quickstart-windows  

Run gcloud as administrator  
gcloud components install kubectl  

#### Update kubectl and minikube
Run gcloud as administrator  
gcloud components update  

#### Download minikube 
Download the minikube installer for windows https://kubernetes.io/docs/tasks/tools/install-minikube/  
Run the installer.  

Open powerShell or cmd and test that minikube works: ```minikube version```  
Run minikube commands from powerShell.  

 
