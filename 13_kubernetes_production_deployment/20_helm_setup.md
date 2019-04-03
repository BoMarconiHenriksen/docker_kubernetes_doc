# Helm Setup
We need to set up one more thing in the production before we can deploy our application.  
We have to install the ingress nginx as a seperate service.  
https://kubernetes.github.io/ingress-nginx/deploy/#using-helm  
#### Helm
*Helm* is a program that we can use to administer 3.part software *inside* our Kubernetes cluster.  
https://github.com/helm/helm  
When we install Helm we get two pices of software.  
*A Helm Client* - A CLI tool.  
*A Tiller Server* - A server running inside our Kubernetes cluster responsible for modifying our cluster and installing diffrent objects inside the cluster.  
### Installing Helm
1. Click the quick start guide in the readme file https://github.com/helm/helm  
2. Click install helm and scroll down to from script.  
3. In the cloud console on google cloud run.  
```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > get_helm.sh  
chmod 700 get_helm.sh  
./get_helm.sh  
!DO NOT RUN HELM INIT # We need to do some set up before!  
```
4. Scroll down to the GKE section.  
We'll done the setup in the next section.  
