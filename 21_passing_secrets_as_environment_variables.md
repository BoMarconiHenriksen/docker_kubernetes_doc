# Passing Secrets as Environment Variables
We have to add the secret to the server-deployment and postgres-deployment.  
### server-deployment.yaml
Add this to the env in the bottom.  
```
- name: PGPASSWORD
	valueFrom:
		secretKeyRef:
		name: pgpassword
		key: PGPASSWORD # The key is what was created with the imperative command
```
### postgres-deployment.yaml
```
env:
	- name: PGPASSWORD
		valueFrom:
			secretKeyRef:
			name: pgpassword
			key: PGPASSWORD # The key is what was created with the imperative command
```
