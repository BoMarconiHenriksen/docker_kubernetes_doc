# Setting Environment Variables
1. In the Elastic Beanstalk go to the configuration.  
2. In the software card select modify.  
3. Scroll down to the environment properties and enter this(from the api service in the docker-compose file):  
Name: REDIS_HOST  
Value: (the url of the running elastic cache instance. Click services and right click ElasticCache and open in new tab. Click redis and expand the instance. In the primary endpoint copy the url without the :port).  
Name: REDIS_PORT  
Value: ```<enter port number from redis page. Last number of url>```  
Name: PGUSER  
Value: ```<username from postgres db instance>```  
Name: PGPASSWORD  
Value: ```<username from postgres db instance>```  
Name: PGHOST  
Value: ```<Go to RDS dashboard. Click dbInstance. Open the db instance. Copy the endpoint in the connect & security section>```  
Name: PGDATABASE  
Value: ```<username from postgres db instance>```  
Name: PGPORT  
Value: ```<Go to RDS dashboard. Click dbInstance. Open the db instance. Copy the port in the connect & security section>```  
4. Click apply.  
> All our instance will have access to the environment variables.  
