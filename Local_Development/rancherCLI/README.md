# RancherCLI
### Install
Download rancherCLI file https://github.com/rancher/cli  
Add it as an enviromental variable.  
Open a new terminal window and write ```rancher --version```.  
### Create Token
1. Login to Rancher.  
2. Select user avatar(the small image top right corner) and click API  Keys.  
3. Click Add Key.  
4. Save the keys a secure place like your password manager.  
### Connect to Rancher from cmd
1. Open a terminal window.  
2. ```rancher login https://<Rancher endpoint> -t your-secret-bearer-token```  
3. ```rancher kubectl get all```  
