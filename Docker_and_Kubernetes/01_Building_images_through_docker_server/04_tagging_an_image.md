# Tagging an Image
Instead of using id you can tag the image and refer to the tag when using docker commands.  
```
docker build -t <docker id>/<repo or project name>:<version> .
docker build -t bomarconi/redis:latest .

docker run bomarconi/redis
```
