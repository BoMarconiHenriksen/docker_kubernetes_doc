# Node Server Setup
1. mkdir simpleweb  
2. cd simpleweb  
3. code .
4. Create a file called ```package.json```
5. Add this to the file you just created.  
```
{
    "dependencies": {
        "express": "*"
    },
    "scripts": {
        "start": "node index.js"
    }
}
```
6. Create a new file called ```index.js```
7. Add this to the index.js file.  
```
const express = require('express');

const app = express();

app.get('/', (req, res) => {
    res.send('Hi there');
});

app.listen(8080, () => {
    console.log('Listening on port 8080');
});
```
8. Create a Dockerfile.  
9. Remember to copy the build folder.  
10. In the Node_web_project folder write ```docker build .```  or ```docker build bomarconi/simpleweb .```
11. localhost:8080 -> does not work see next section.  
