# Unique Deployment images
Build the images and push them to docker hub.  
```
# Building the images
docker build -t bomarconi/multi-client -f ./client/Dockerfile ./client
docker build -t bomarconi/multi-server -f ./server/Dockerfile ./server
docker build -t bomarconi/multi-worker -f ./worker/Dockerfile ./worker

# Push the images to docker hub
docker push bomarconi/multi-client
docker push bomarconi/multi-server
docker push bomarconi/multi-worker

# Apply the images to kubernetes
kubectl apply -f k8s
```
> We have to tag the images with a specific version. Se next section!  
