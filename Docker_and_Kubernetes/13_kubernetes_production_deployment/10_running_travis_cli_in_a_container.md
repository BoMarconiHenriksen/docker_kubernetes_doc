# Running Travis CLI in a Container
We are going to use Travis CLI to encrypt the json file.  
We have to install Ruby for this but it's a pain. So we are going to get a Docker image that has ruby installed, then we can install travis cli in there.  
##### The commands we are going to use:  
```
docker run -it -v $(pwd):/app ruby:2.3 sh # On windows: docker run -it -v ${pwd}:/app ruby:2.3 sh  
gem install travis 
gem install travis  
travis login  
Copy json file into the volumed directory so we can use it in the container.  
travis encrypt-file service-account.json -r bomarconi/multi-k8s  
```
1. cd into your git repository for the project.  
2. docker run -it -v ${pwd}:/app ruby:2.3 sh  
3. ls # Check that the app folder is there.  
4. cd app  
5. ls # Check that you have the project folders.  
6. gem install travis  
7. travis # Check the installation and enter n.  
