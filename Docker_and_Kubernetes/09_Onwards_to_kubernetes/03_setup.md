# Setup on windows
https://www.c-sharpcorner.com/article/getting-started-with-kubernetes-on-windows-10-using-hyperv-and-minikube/  

#### Install minikube on Hyper-V
Follow this tutorial.  
https://docs.docker.com/machine/drivers/hyper-v/#2-set-up-a-new-external-network-switch-optional  

After the restart run this command. Be sure to change ```--hyperv-virtual-switch="Primary Virtual Switch"``` if you gave the switch another name.  

##### Run these commands after installing kubectl and minikube
minikube start --vm-driver=hyperv --hyperv-virtual-switch="Primary Virtual Switch" --v=7 --alsologtostderr  
(you can add a memory flag: --memory 4096)  

minikube status  
minikube delete 

#### Install kubectl
https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-windows  
Download the latest version of kubectl. See the link.  
Create a folder on your machine called .kubectl  
Move the downloaded file to that folder.  
Create a path to the folder and move it higher than the docker path if you have installed docker desktop.  
Open a terminal and write kubectl version  

#### Alternative is to install kubectl with goggle cloud sdk for windows.  
https://cloud.google.com/sdk/docs/quickstart-windows  

Run gcloud as administrator  
gcloud components install kubectl  

#### Download minikube 
Download the minikube installer for windows https://kubernetes.io/docs/tasks/tools/install-minikube/  
Run the installer.  

Open powerShell or cmd and test that minikube works: ```minikube version```  
Run minikube commands from powerShell.  
minikube start --vm-driver=hyperv --hyperv-virtual-switch="Primary Virtual Switch" --v=7 --memory=6000 --alsologtostderr  
#### Update kubectl and minikube
Run gcloud as administrator  
gcloud components update  
