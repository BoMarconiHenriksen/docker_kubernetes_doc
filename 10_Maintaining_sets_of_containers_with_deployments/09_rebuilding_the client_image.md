# Rebuilding the Client Image
Change the code in the client, rebuild it and push it to docker hub.  
1. cd into multi-docker.  
2. Open your code editor.  
3. Go to src and open App.js  
4. Change the h1 tag to Fib calculator version 2  
5. docker build -t bomarconi/multi-client .  # Be sure to be in the client directory.  
6. docker push bomarconi/multi-client  
