# Setup on windows
https://kubernetes.io/docs/tasks/tools/install-minikube/  
https://chocolatey.org/install#installing-chocolatey  
1. Install kubectl https://kubernetes.io/docs/tasks/tools/install-kubectl/  
2. Install minikube  

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
