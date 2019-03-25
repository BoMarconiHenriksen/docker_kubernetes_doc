# Production Multi-Container Deployments
##### Multi Container Setup
1. Push code to github.  
2. Travis automatically pulls repo.  
3. Travis builds a *test* image, test code.  
4. Travis builds *prod* images.  
5. Travis pushes build *prod* images to Docker Hub.  
6. Travis pushes project to AWS EB.  
7. EB pulls images from Docker Hub and deploys.  
