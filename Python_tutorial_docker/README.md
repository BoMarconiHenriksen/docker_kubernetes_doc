# Docker Tutorial
https://docs.docker.com/get-started/part2/  

### Lav en Dockerfile
En Dockerfile definer dit miljø i containeren.  
```
# Use an official Python runtime as a parent image
FROM python:2.7-slim

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```
### Build appen
Lav et docker image med build komandoen. Vi giver vores image et navn vha --tag eller -t.  
```
docker build --tag=friendlyhello:v0.0.1 .
```
Tjek din lokale docker image registry.  
```
docker image ls
```
### Run the app
local host 4000 og containeren publishes til port 80.  
```
docker run -p 4000:80 friendlyhello

curl http://localhost:4000
http://localhost:4000/
```
### Stop the container
ctrl + c
##### On windows
```
docker container ls
docker container stop `<Container NAME or ID>`
```
### Run the app in the background in detached mode
```
docker run -d -p 4000:80 friendlyhello
docker container ls
```