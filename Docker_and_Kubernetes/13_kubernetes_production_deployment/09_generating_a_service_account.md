# Generating a Service Account
This is what we are going to do. Login into google console.  
1. Create a service account.  
2. Download service account credentials in a json file.  
3. Download and install the Travis CLI.  
4. Encrypt and upload the json file to our Travis account.  
5. In travis.yml, add code to unencrypt the json file and load it into GCloud SDK.  
---
Go to the google console.  
1. Click navigation menu and IAM & admin.  
2. Click service accounts and click create service account.  
Name: travis-deployer
Role: Kubernetes Engine --> Kubernetes Engine Admin.  
select furnish a new private key(json).  
The file that was download is never going to be exposed to the outside world.  
