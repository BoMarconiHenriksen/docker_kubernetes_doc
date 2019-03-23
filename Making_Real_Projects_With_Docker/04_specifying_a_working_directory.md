# Specifying a Working Directory
COPY places the files in the root directory. Best practice is to specify a working directory.  

##### You can debug or see the files and folders indside the container.  
```docker run -it bomarconi/simpleweb sh``` and then ls.  

##### Use the workdir instruction
```WORKDIR <any following command will be executed relative to this path>```
```WORKDIR /usr/app```
Check that the working directory was created. Remember to build it first.  
```
docker ps  
docker exec -it <container id> sh  
```
