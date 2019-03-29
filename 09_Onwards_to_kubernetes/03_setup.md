# Setup on windows
https://kubernetes.io/docs/tasks/tools/install-minikube/  
https://chocolatey.org/install#installing-chocolatey  


1. Install kubectl https://kubernetes.io/docs/tasks/tools/install-kubectl/  
2. Install minikube  

### Install kubectl
1. Get the latest version here https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl  
2. Create a folder called .kube  
3. Set the path to the .kube folder in a system environment variable.  

### Install Minicube
https://kubernetes.io/docs/tasks/tools/install-minikube/
To run Minikube on Windows, you need to install Hyper-V first(if you have install docker it it installed). .
You can install it with chocolatey ```choco install minikube kubernetes-cli``` or  
download it https://github.com/kubernetes/minikube/releases/tag/v1.0.0 add the file to a folder and make a path in an environment variable.  


### Install minikube on Hyper-V
1. In powershell(open as admin) write: *Get-NetAdapter*  
Pick one that has Up in the Status column.  
New-VMSwitch –Name "minikube" –AllowManagement $True –NetAdapterName "INSERT_HERE_ADAPTER"  
Example  
New-VMSwitch –Name "minikube" –AllowManagement $True –NetAdapterName "Ethernet"
> Please note that --vm-driver=hyperv --hyperv-virtual-switch=minikube is necessary only for the first start. If you wish to change the driver or the memory you have to minikube destroy and recreate the VM with the new settings.  
2. minikube start  
If for any reason minikube fails to start up, you can debug it with:  
```
minikube delete  
minikube start --vm-driver=hyperv --hyperv-virtual-switch=minikube --v=7 --alsologtostderr  
```
3. Test it with *kubectl get nodes* (You should be able to see a single node in Kubernetes.)  

For more information check https://learnk8s.io/blog/installing-docker-and-kubernetes-on-windows/  
