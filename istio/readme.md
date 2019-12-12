# Istio
# Installation of Istio in Rancher
When you enable Istio in Rancher add the LoadBalancer(in the section enable ingress gateway) when using MetalLB. This will automatically give you an ip address.  
### Get External Ip
```kubectl get svc istio-ingressgateway -n istio-system```  
