# Overwrite Dockerfile Selection
The context option specifies where we want the files and folders for this image to be pulled from.  
We want the curent working directory.  
The dockerfile option is the location of the Dockerfile that is going to be used to construct the image.  
Look in the curent working directory and find the file Dockerfile.dev.  
```
build: 
      context: .
      dockerfile: Dockerfile.dev
```
Run ```docker-compose up```
