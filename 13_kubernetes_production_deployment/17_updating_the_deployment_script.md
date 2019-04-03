# Updating the Deployment Script
First we add some code to our .tavis.yml file so that we can determin the curent git sha for our repository and export as an environment variable so that we can use it inside our deploy file.  
1. Open .travis.yml  
2. In the top of the file just below services add.  
```
env:
  global:
    # Get the current commit sha and store it as an environment variable called sha
    - SHA=$(git rev-parse HEAD)
    # Configure google cli so it's does not show prompts
    - CLOUDSDK_CORE_DISABLE_PROMPTS=1
```
#### Open deploy.sh
```
# Building the images and add 2 tags for each image
docker build -t bomarconi/multi-client:latest -t bomarconi/multi-client:$SHA -f ./client/Dockerfile ./client
docker build -t bomarconi/multi-server:latest -t bomarconi/multi-server:$SHA -f ./server/Dockerfile ./server
docker build -t bomarconi/multi-worker:latest -t bomarconi/multi-worker:$SHA -f ./worker/Dockerfile ./worker

# Push the images to docker hub
docker push bomarconi/multi-client:latest
docker push bomarconi/multi-server:latest
docker push bomarconi/multi-worker:latest

docker push bomarconi/multi-client:$SHA
docker push bomarconi/multi-server:$SHA
docker push bomarconi/multi-worker:$SHA

# Apply the images to kubernetes
kubectl apply -f k8s

# Make sure that we use the latest image for each container
kubectl set image deployments/server-deployment server=bomarconi/multi-server:$SHA
kubectl set image deployments/client-deployment client=bomarconi/multi-client:$SHA
kubectl set image deployments/worker-deployment worker=bomarconi/multi-worker:$SHA
```
