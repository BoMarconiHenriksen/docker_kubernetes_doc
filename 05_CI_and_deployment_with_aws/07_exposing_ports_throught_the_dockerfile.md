# Exposing Ports Through the Dockerfile
No ports outside the container is exposed. We have to setup that ourselves.  
1. Go to the Dockerfile for production deployments.  
2. Add this code.  
```
FROM nginx
# This is to expose the port for beanstalk when you deploy.
EXPOSE 80
```
3. Push the changes.  

#### Build Still Failing?

If you still see a failed deployment, try the following two steps:  
##### Fix One:
The npm install command frequently times out on the t2.micro instance that we are using.  An easy fix is to bump up the instance type that Elastic Beanstalk is using to a t2.small.  

Note that a t2.small is outside of the free tier, so you will pay a tiny bit of money (likely less than one dollar if you leave it running for a few hours) for this instance.  Don't forget to close it down!  Directions for this are a few videos ahead in the lecture titled 'Environment Cleanup'.  

##### Fix Two:
Try editing the 'COPY' line of your Dockerfile like so:  
```COPY package*.json ./```  
> Sometimes AWS has a tough time with the '.' folder designation and prefers the long form ./  
