# Unnecessary Rebuilds
When you change code in your app the browser does not show the changes when you refresh.  
```docker run -p 8080:8080 bomarconi/simpleweb```
Change the text in index.js to Bye there.  
```docker build -t bomarconi/simpleweb .```
What happens is that npm install runs again.  
### Solution so that npm install does not run when you change source code
#### Chache busting and rebuilds
In the Dockerfile before npm install be sure to only copy the package.json file.  
```COPY ./package.json ./```
After the npm install copy the application to the working directory.  
```COPY ./ ./```
npm install will only be executed if we change the package.json file or any of the steps before npm install.  

> Be sure to copy only the bare minimum for each step.
