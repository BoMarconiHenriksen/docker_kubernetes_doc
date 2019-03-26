# Adding Container Definitions to Dockerrun
1. In the project root add a file called ```Dockerrun.aws.json```  
2. Add this code.  
```
{
    "AWSEBDockerrunVersion": 2,
    "containerDefinitions": [
        {
            "name": "client",
            "image": "bomarconi/multi-client",
            "hostname": "client",
            "essential": false
        },
        {
            "name": "server",
            "image": "bomarconi/multi-server",
            "hostname": "api",
            "essential": false
        },
        {
            "name": "worker",
            "image": "bomarconi/multi-worker",
            "hostname": "worker",
            "essential": false
        },
        {
            "name": "nginx",
            "image": "bomarconi/multi-nginx",
            "essential": true,
            "portMappings": [
                {
                    "hostPort": 80,
                    "containerPort": 80
                }

            ],
            "links": ["client", "server"]
        }
        
    ]
}
```
*name* is a name for the container. It does not have to be identical to anything. It will show up on a dashboard so you can identify it.  
*hostname* is the same as the name of the service in the docker-compose file. You can access the other containers by reference the hostname.  
*essential* this container is not considered essential. If it's true then if the container crashes then will all the other containers close down at the same time. One container has to be marked essential!  
*hostPort* open a port on the host(the machine) that is hosting all our containers and map that to *containerPort* 80 inside our container.  
*links* has to refer to the container name. I Elastic Beanstalk we have to make links between the containers so nginx has a link to the server and a link to the client.  
Remember to validate your json.  
