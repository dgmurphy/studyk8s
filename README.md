# studyk8s
## ConfigMap from File
kubectl create configmap postgresql-config --from-file=config/ 

## Secrets from File
kubectl create secret generic postgresql-secrets --from-file=secrets/ 


## Deploy
Create:
* configmap
* secrets
* storage (local)
* deployment
* service

## Test
* exec into postgres pod
* postgres=# SHOW ssl;
* from host: psql dbname username
* ssl: https://stackoverflow.com/questions/14021998/using-psql-to-connect-to-postgresql-in-ssl-mode
