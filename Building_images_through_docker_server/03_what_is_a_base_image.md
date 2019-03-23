# What is a Base Image?
### Analogy
> Writing a dockerfile is like being given a computer with no OS and being told to install Chrome.  

### The Build Process in Detail
In the output you get a step for each instruction in the Dockerfile.  
#### Intermedia container
1. For step 2 and 3 an intermedia container was created.  
2. The run command goes one step back and look at the image that was downloaded in step one.  
3. Then it takes the image and create a new container out of it so in memory we temporary got an image.  
4. Then the update command is executed in the temporary container as a primary process.  
5. After the installation it stoped the container and took a filesystem snapshot of it and saves it with a temporary image.  

1. For step 3 it again looks at the image generated at step 2.  
2. Generate a new temporary container out of it.  
3. Then it's told it's primary command.  
4. Then takes a snapshot of the system with the primary command and shut it down.  
5. That last snapshot is the final image that is being used as a container.  

The end result is an image with an id. That has a full filesystem snapshot and a specified startup command.  

> Remember for each command instruction it takes the image that was reated in the previous step and creates a new temporary container.

### Rebuild with cache
This is what gives Docker so good performance.  
If nothing has changed from the last time we run docker build then docker use the cache. This also applies for updating with the run instruction.  
> If the order of the instructions change it has to build again and do not use the cache. So changes has to be placed as far down as possible.  
