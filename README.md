# studyk8s
## ConfigMap from File
kubectl create configmap postgresql-config --from-file=config/ 

## Secrets from File
kubectl create secret generic postgresql-secrets --from-file=secrets/ 


## Deploy
Create:
* storage (local)
* configmap
* secrets
* deployment
* service (with NodePort)

## Test
* exec into postgres pod
* postgres=# SHOW ssl;
* from host: psql -h localhost -U [user] --password -p [nodeport] [dbname]
* `psql -h localhost -U postgresadmin1 --password -p 31070 postgresdb`
* ssl: https://stackoverflow.com/questions/14021998/using-psql-to-connect-to-postgresql-in-ssl-mode


# References
https://purnapoudel.blogspot.com/2018/09/how-to-configure-postgresql-with-ssl-tls-on-kubernetes.html

https://severalnines.com/database-blog/using-kubernetes-deploy-postgresql