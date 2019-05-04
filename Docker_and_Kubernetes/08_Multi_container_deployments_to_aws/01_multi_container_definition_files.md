# Multi-Container Definition Files
We now have diffrent folders on our docker hub account and each have a single docker file.  
So we have to tell Elastic Beanstalk how to treat our project.  

In our project directory we are going to create a ```Dockerrun.aws.json``` file. It's going to tell Elastic Beanstalk where to pull all our images from, what reasurces to allocate to each one, how to setup port mappings and some accociate information.  
The file is going to be a little bit like the *docker-compose.yml* file.  
> The ```Dockerrun.aws.json``` is going to contain *container definitions*.  
