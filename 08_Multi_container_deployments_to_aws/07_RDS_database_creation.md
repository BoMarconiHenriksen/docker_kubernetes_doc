# RDS Database Creation
1. Search rds and go to the RDS dashboard.  
2. Click create databse.  
3. Select postgres and check the *Only enable options eligible for RDS Free Usage Tier* and click next.  
4. Scroll down to settings and enter:  
DB instance identifier: multi-docker-postgres  
Master username: postgres
Master password: postgrespassword
> Username and password has to be passed to the api service in the docker-compose file.  
5. Click next.  
6. Scroll down to database options.  
7. Database name: fibvalues (has to match up with the database name in the api service in the docker-compose file.).  
8. Click create database.  
9 Click all db instances to see the status of the new database.  
