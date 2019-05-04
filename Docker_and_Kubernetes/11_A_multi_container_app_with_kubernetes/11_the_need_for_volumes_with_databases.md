# The need for Volumes with Databases
### Postgres(PVC) Persistence Volume Claim
Volume is the same as we worked with earlier. Share files from host computer with docker container.  
Postgres takes data in and write it to a filesystem.  
If a postgres container crashes then everything in the container will be lost.  
The solution to this is volume.  
Postgres will write the data to a volume that exist outside the dockerfile.  
