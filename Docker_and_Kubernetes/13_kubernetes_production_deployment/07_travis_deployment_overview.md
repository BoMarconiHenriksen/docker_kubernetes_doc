# Travis Deployment Overview
This is whats going to happen inside the Travis config file.  
1. Install Google Cloud SDK CLI.  
2. Configure the SDK with out Google Cloud auth info.  
3. Login to Docker CLI.  
4. Build the 'test' version of multi-client.  
5. Run tests.  
6. If test are successful, run a script to deploy newest images.  
7. Build all our images, tag each one, push each to docker hub.  
8. Apply all configs in the k8s folder.  
9. Imperatively set latest images on each deployment.  
