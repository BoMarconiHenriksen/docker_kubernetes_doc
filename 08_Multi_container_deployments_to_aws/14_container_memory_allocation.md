# Container Memory Allocation
For everyone of our container definitions we need to setup a memory option.  
Tell E.B. how much ram to allocate to each dockerfile. Specify amout of memory in megabyte for each container in the Dockerrun.aws.json file.  
In a real app you need to figure hov mush memory you have to allocate. Use stackoverflow...  
```
{
    "AWSEBDockerrunVersion": 2,
    "containerDefinitions": [
        {
            "name": "client",
            "image": "bomarconi/multi-client",
            "hostname": "client",
            "essential": false,
            "memory": 128
        },
        {
            "name": "server",
            "image": "bomarconi/multi-server",
            "hostname": "api",
            "essential": false,
            "memory": 128
        },
        {
            "name": "worker",
            "image": "bomarconi/multi-worker",
            "hostname": "worker",
            "essential": false,
            "memory": 128
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
            "links": ["client", "server"],
            "memory": 128
        }

    ]
}
```
Push the changes to your master branch on github.  
