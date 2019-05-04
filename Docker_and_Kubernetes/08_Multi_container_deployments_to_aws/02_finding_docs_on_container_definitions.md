# Finding Docs on Container Definitions
In AWS Elastic Beanstalk does not really know how to run containers. It uses Amazon Elastic Container Service(ECS).  
ECS uses task definition which is instructions on how to run one single container. They are almost identical with the container definitions from the Dockerrun file.  
To customize your Dockerrun file you have to look at the docs for task definitions.  
https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html#container_definitions  
