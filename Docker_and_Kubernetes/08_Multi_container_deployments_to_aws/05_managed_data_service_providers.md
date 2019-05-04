# Managed Data Service Providers
When going to production our architecture is going to change.  
In the Elastic Beanstalk instance we will have the Nginx server in front of the webapp, an Express server, Nginx with production files and a worker. Outside the instance we will have the database and Redis.  
Postgres willl be replaced with AWS Relational Database Service(RDS) and Redis will be replaced with AWS Elastic Cache.  
### Advantages of AWS Elastic Cache and AWS Relational Databases
1. Automatically creates and maintains Redis instances for you. Is configured for you.  
2. Super easy to scale.  
3. Built in logging and maintenance.  
4. Probably better security than we can do.  
5. Easier to migrate out of EB with.  
6. AWS Relational Databases: Automated backups and rollbacks.  
