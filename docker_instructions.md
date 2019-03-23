# Docker instructions
### The most important instructions
#### FROM
What image do we want to use as a base.  
#### RUN
Execute commands while we are preparing the image.  
#### CMD (Command Instruction)
What should be executed when our image is used to start up a new container.  
---
#### Copy the build folder or other files
```COPY <path to folder to copy from on your machine relativ to build context(the .)> <place to copy stuff to inside the container>```
```COPY ./ ./``` The first ./ means that we execute docker build . in the build folder.  
#### Specifying a Working Directory
```WORKDIR <any following command will be executed relative to this path>```
```WORKDIR /usr/app```


