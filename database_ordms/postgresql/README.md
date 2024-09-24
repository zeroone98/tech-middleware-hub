[toc]

# 分析

简称pg

未来3年内数据库的趋势是postgresql

app操作需要数据库SQL, 区块链本身没有提供SQL功能, 区块链浏览器也只是展示常规数据和操作, 不足以支撑app



# 架构

pgpool->pg(repmgr)(1master+2slaver)



# 部署

```
namespace=test-pg
```



```
kubectl label nodes $(hostname) zeroone.io/pg-


kubectl label nodes $(hostname) zeroone.io/pg=y
```



```
helm -n ${namespace} uninstall pg
kubectl -n ${namespace} delete pvc data-pg-postgresql-ha-postgresql-0 data-pg-postgresql-ha-postgresql-1 data-pg-postgresql-ha-postgresql-2


helm upgrade --install pg ../../postgresql-ha/ --namespace ${namespace} --create-namespace -f values.yaml
```



```
# postgres
$(kubectl get secret --namespace test-pg pg-postgresql-ha-postgresql -o jsonpath="{.data.password}" | base64 -d)
```



```
kubectl -n ${namespace} get pvc
kubectl -n ${namespace} get pod

kubectl -n ${namespace} logs -f --tail 300 deploy/db-postgresql-ha-pgpool
kubectl -n ${namespace} logs -f --tail 300 pg-postgresql-ha-postgresql-0
kubectl -n ${namespace} logs -f --tail 300 pg-postgresql-ha-postgresql-1
kubectl -n ${namespace} logs -f --tail 300 pg-postgresql-ha-postgresql-2

kubectl -n ${namespace} delete pod pg-postgresql-ha-postgresql-0
```

