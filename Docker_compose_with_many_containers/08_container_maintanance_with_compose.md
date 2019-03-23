# Container Maintenance with Compose
How do you deal with containers that crash?  
1. In index.js add the following code so the server crash everytime someone visits the app.  
```
const process = require('process');

app.get('/', (req, res) => {
  process.exit(0); // Add this line.
  client.get('visits', (err, visits) => {
    res.send('Number of visits is ' + visits);
    client.set('visits', parseInt(visits) + 1);
  });
});
```
2. Make sure that we rebuild the container write: ```docker-compose up --build```

The result is that the node container crash.  
