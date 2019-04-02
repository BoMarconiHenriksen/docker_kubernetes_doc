# Encrypting a Service Account File
1. travis login  
2. Copy the json file to the root of the project directory.  
3. Rename the file to service-account  
4. ls # Check that you have the service-account.json file.  
5. travis encrypt-file service-account.json -r BoMarconiHenriksen/multi-k8s # The repo from travis.  
6. Copy the command that was printed and go to the .travis.yml file.  
7. Just after the before install paste the command.  
8. It's is safe to add the service-account.json.enc file to the repository.  
9. IMPORTANT! Delete the service-account.json file. 
10. exit  
11. git add .  
12 git commit -m "Added encrypted service account file."  
