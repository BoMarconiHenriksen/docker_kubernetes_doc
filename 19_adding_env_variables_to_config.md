# Adding Environment Variables to Config
The Host environment variables will tell how the multi-server and multi-worker will connect to redis and postgres.  
We want to create a link from the multi-worker pod to the clusterIP service for the redis deployment.  
Open the file ```redis-cluster-ip-service.yaml``` the name in the metadata is the host name. Like an url.  
---
### worker-deployment file
1. open ```worker-deployment.yaml```  
2. scroll down to the template section and add the env to the containers section.  
```
containers:
- name: worker
	image: bomarconi/multi-worker
	env:
	- name: REDIS_HOST
		value: redis-cluster-ip-service # Name of the clusterIP service for the redis pod
	- name: REDIS_PORT
		value: 6379
```
### server-deployment file
1. Open ```server-deployment.yaml```  
2. scroll down to the template section and add the env to the containers section.  
```
containers:
	- name: server
		image: bomarconi/multi-server
		ports:
		- containerPort: 5000
		env:
		- name: REDIS_HOST
			value: redis-cluster-ip-service
		- name: REDIS_PORT
			value: 6379
		- name: PGUSER
			value: postgres
		- name: PGHOST
			value: postgres-cluster-ip-service
		- name: PGPORT
			value: 5432
		- name: PGDATABASE
			value: postgres
```
