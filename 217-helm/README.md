# Exercise commands

## Installation
Add repo of Bitnami (if not present)
```
helm repo add my-repo https://charts.bitnami.com/bitnami
```

Install chart with storageClass available in cluster

```
helm install mysql my-repo/mysql  --set global.storageClass=local-nfs
```


## Removal
```
helm uninstall mysql
```

```
k delete pvc $(k get pvc --selector=app.kubernetes.io/name=mysql --output=jsonpath={.items..metadata.name})
```