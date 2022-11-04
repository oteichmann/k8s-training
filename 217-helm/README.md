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

**Alternative approach**
Fetch values yaml for configuration
```
helm inspect values my-repo/mysql > mysql-helm-chart-config.yaml
```

Set desireded properties, sucha as storageClass in config YAML.

Run install while referencing config file.
```
helm install -f mysql-helm-chart-config.yaml mysql my-repo/mysql
```

## Removal
```
helm uninstall mysql
```

```
k delete pvc $(k get pvc --selector=app.kubernetes.io/name=mysql --output=jsonpath={.items..metadata.name})
```