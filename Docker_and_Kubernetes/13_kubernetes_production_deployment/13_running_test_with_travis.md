# Running Test with Travis
We have to set up our login to docker in Travis.  
1. Go to the multi-k8s project at travis.  
2. Click settings and then more options.  
3. Scroll down to environment variables and add.  
```Name: DOCKER_USERNAME```  
```Value: <docker id>```  
```Name: DOCKER_PASSWORD```  
```Value: <docker password>```  

```
- echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
```
### Build the 'test' version of multi-client
```
# Build the test image. Is nestet in the client folder
  - docker build -t bomarconi/react-test -f ./client/Dockerfile.dev ./client
```
### Run the tests
```
script:
  # -- -- coverage means no watchmode
  - docker run bomarconi/react-test npm test -- --coverage
```
