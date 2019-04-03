# Unique Tags for Build Images
We have to change the tags for each build or the images will not be deployed.  
We are going to tag each image two times.  
##### First tag
First we tag it with latest. We do this to be sure that if someone clone the project always will get the latest images without having to worry about getting the right git_sha. Usefull if you get a new developer.  
##### Secound tag
Then we tag it with git_sha(a unique id that we get when we commit and identifies the current changes inside our codebase).  
```git rev-parse HEAD``` will print the current sha for the latest commit.  
```git log``` will print the shas for all the commits.  
### Benefit of using git sha
We discover our app is breaking. What is the exact state of the code base that our deployments are running? -->  
Deployment is running multi-client:3453452 -->  
```git checkout 3453452``` -->  
Debug the app knowing the exact code that is running.  

!(diffrent_tags)[diffrent_tags.png]  
