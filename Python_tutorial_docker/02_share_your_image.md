# Share Your Image
https://docs.docker.com/get-started/part2/  

docker login  
### Tag the images
```
docker tag image username/repository:tag
docker container ls
```
### Publish the image
```
docker push username/repository:tag
```
### Docker run
Du kan nu bruge docker run, og kører din app fra en hvilken som helst masking.  
```
docker run -p 4000:80 username/repository:tag
```
