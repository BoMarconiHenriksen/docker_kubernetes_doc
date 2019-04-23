# Skaffold
https://github.com/GoogleContainerTools/skaffold  
##### Fast local Kubernetes Development
Optimized source-to-k8s - Skaffold detects changes in your source code and handles the pipeline to build, push, and deploy your application automatically with policy based image tagging and highly optimized, fast local workflows.  

In practice, Skaffold can:  
1. Detect changes in the source code and automatically build, push and deploy.  
2. Automatically update image tags, so you don’t have to do that manually in the Kubernetes manifest files.  
3. Build/deploy/push different applications at once, so it is a perfect fit for microservices too,
support both development and production environment, by running the manifests only once, or continuously watching for changes.  

We will use it locally.  
### Install skaffold on windows
https://skaffold.dev/docs/getting-started/#installing-skaffold  
1. Make sure docker, minikube and kubectl is installed.  
2. Download the latest realease https://github.com/GoogleContainerTools/skaffold/releases  
3. Create a folder and place the file you downloaded in the folder.  
4. Change the name of the file to skaffold.exe.  
5. Create an environment variable with a path to your skaffold folder.  
6. In a new terminal window write skaffold version.  

### Setting up a config file for skaffold
https://skaffold.dev/docs/references/yaml/  
1. cd into the folder where you have your yml config files.  
2. ```skaffold init -f skaffold.yml``` # Choice the dockerfile to build each image and skaffold will autogenerate your skaffold.yml file.  
3. 

skaffold dev -p dev -v=info  
skaffold dev  

### Commands for our system
docker login  
skaffold dev -p dev  
skaffold dev -p prod  
