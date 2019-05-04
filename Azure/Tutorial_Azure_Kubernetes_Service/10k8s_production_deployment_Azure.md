# AKS Deployment on Azure
### Linking Github to Travis
1. Go to Travis.  
2. Go to repositories and enable multi-k8s.  
3. Go to the project.  
### Travis Deployment Overview
This is whats going to happen inside the Travis config file.  
1. Install Azure CLI.  
2. Configure the Azure CLI with out Azure auth info.  
3. Login to Docker CLI.  
4. Build the 'test' version of the app.  
5. Run tests.  
6. If test are successful, run a script to deploy newest images.  
7. Build all our images, tag each one, push each to docker hub.  
8. Apply all configs in the k8s folder.  
9. Imperatively set latest images on each deployment.  
https://webhint.io/docs/user-guide/development-flow-integration/travis-and-azure/  
https://docs.travis-ci.com/user/deployment/azure-web-apps/  

# Install Azure CLI
sudo: required
services:
  - docker
before_install:
    # Download and install Azure CLI. 
    - AZ_REPO=$(lsb_release -cs) && echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | sudo tee /etc/apt/sources.list.d/azure-cli.list
    - curl -L https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    - sudo apt-get install apt-transport-https
    - sudo apt-get update && sudo apt-get install azure-cli
    # Download and install kubectl
    - curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
    - touch /etc/apt/sources.list.d/kubernetes.list 
    - echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
    # Log in to Azure with Service Principal Creadentials
    - az login --service-principal -u $AZURE_SERVICE_PRINCIPAL -p $AZURE_SERVICE_PRINCIPAL_PASSWORD --tenant $AZURE_TENANT
    - az webapp deployment slot swap -g RESOURCEGROUP -n SITE --slot SLOTNAME
TODO ENCRYPTION OF ENV VARIABLES!  
For kube apply: Add the -R flag to recursively process directories.  



