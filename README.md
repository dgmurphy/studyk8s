# studyk8s
## ConfigMap from File
kubectl create configmap postgresql-config --from-file=config/ 

## Secrets from File
kubectl create secret generic postgresql-secrets --from-file=secrets/ 


## Deploy
Create:
* storage - local
* configmap - postgres.conf & pg_hba.conf
* secrets - tls certs
* deployment - has creds configmap
* service - expose NodePort

## Test
* exec into postgres pod
* postgres=# SHOW ssl;
* from host: psql -h localhost -U [user] --password -p [nodeport] [dbname]
* no ssl: `psql -h localhost -U postgresadmin --password -p 31070 postgresdb`
* ssl: `psql -U postgresadmin  "sslmode=require host=localhost port=32658 dbname=postgresdb"`


# References
https://purnapoudel.blogspot.com/2018/09/how-to-configure-postgresql-with-ssl-tls-on-kubernetes.html

https://severalnines.com/database-blog/using-kubernetes-deploy-postgresql

