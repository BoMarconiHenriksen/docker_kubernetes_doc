# Cert Manager Install
https://github.com/jetstack/cert-manager  

If the Google VM restart you need to install Helm again.  
```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > get_helm.sh  
chmod 700 get_helm.sh 
./get_helm.sh  
##### !DO NOT RUN HELM INIT # We need to do some set up before!  
#### ONLY IF THE NAMESPACE and clusterrolebinding DOES NOT EXITS
kubectl create serviceaccount --namespace kube-system tiller  
kubectl create clusterrolebinding tiller-cluster-role --clusterrole=cluster-admin --serviceaccount=kube-system:tiller

helm init --service-account tiller --upgrade
export PATH="$(echo ~)/helm-v2.6.0/linux-amd64:$PATH"
```
##### Be sure you have the latest kubernetes  
```
##### Install the CustomResourceDefinition resources separately
kubectl apply -f https://raw.githubusercontent.com/jetstack/cert-manager/release-0.8/deploy/manifests/00-crds.yaml

##### Create the namespace for cert-manager
kubectl create namespace cert-manager

##### Label the cert-manager namespace to disable resource validation
kubectl label namespace cert-manager certmanager.k8s.io/disable-validation=true

##### Add the Jetstack Helm repository
helm repo add jetstack https://charts.jetstack.io

##### Update your local Helm chart repository cache
helm repo update

##### Install the cert-manager Helm chart
helm install \
  --name cert-manager \
  --namespace cert-manager \
  --version v0.8.0 \
  jetstack/cert-manager
```
