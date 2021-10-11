# studyk8s
## ConfigMap from File
kubectl create configmap postgresql-config --from-file=config/ 

## Secrets from File
kubectl create secret generic postgresql-secrets --from-file=secrets/ 


## Deploy
Create:
* empty the psql data dir with perms 999:999 (check mount location in storage deploy)
* configmap - postgres.conf & pg_hba.conf
* secrets - tls certs
* storage - local 
* deployment - has creds configmap
* service - expose NodePort

## Test
* exec into postgres pod
* postgres=# SHOW ssl;
* from host: psql -h localhost -U [user] --password -p [nodeport] [dbname]
* no ssl: `psql -h localhost -U postgresadmin --password -p 31070 postgres`
* ssl: `psql -U postgresadmin  "sslmode=require host=localhost port=32658 dbname=postgres"`


# References
https://purnapoudel.blogspot.com/2018/09/how-to-configure-postgresql-with-ssl-tls-on-kubernetes.html

https://severalnines.com/database-blog/using-kubernetes-deploy-postgresql

# Notes
This is the pod user in postgres 10.4

`$ whoami`

 postgres

`$ id`

uid=999(postgres) gid=999(postgres) groups=999(postgres),103(ssl-cert),1000


This is the user in DoD IB 12.7:

`bash-4.4$ id`

uid=26(postgres) gid=26(postgres) groups=26(postgres)
