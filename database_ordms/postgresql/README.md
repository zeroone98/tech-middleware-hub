[toc]

# 分析

简称pg

未来3年内数据库的趋势是postgresql

app操作需要数据库SQL, 区块链本身没有提供SQL功能, 区块链浏览器也只是展示常规数据和操作, 不足以支撑app



# 架构

pgpool->pg(repmgr)(1master+2slaver)



# 部署

命名空间

```
namespace=test-pg
```

划分节点池

```
kubectl label nodes $(hostname) zeroone.io/pg-


kubectl label nodes $(hostname) zeroone.io/pg=y
```

部署

```
helm -n ${namespace} uninstall pg
kubectl -n ${namespace} delete pvc data-pg-postgresql-ha-postgresql-0 data-pg-postgresql-ha-postgresql-1 data-pg-postgresql-ha-postgresql-2
kubectl -n ${namespace} delete -f svc.yaml


helm upgrade --install pg ../../postgresql-ha/ --namespace ${namespace} --create-namespace -f values.yaml
kubectl -n ${namespace} apply -f svc.yaml
```

查看密码

```
# postgres
echo $(kubectl get secret --namespace test-pg pg-postgresql-ha-postgresql -o jsonpath="{.data.password}" | base64 -d)
```

调试

```
kubectl -n ${namespace} get pvc
kubectl -n ${namespace} get pod
kubectl -n ${namespace} get svc

kubectl -n ${namespace} logs -f --tail 300 deploy/db-postgresql-ha-pgpool
kubectl -n ${namespace} logs -f --tail 300 pg-postgresql-ha-postgresql-0
kubectl -n ${namespace} logs -f --tail 300 pg-postgresql-ha-postgresql-1
kubectl -n ${namespace} logs -f --tail 300 pg-postgresql-ha-postgresql-2

kubectl -n ${namespace} delete pod pg-postgresql-ha-postgresql-0
```

本地连接

```
kubectl -n ${namespace} port-forward service/mid-postgresql 5432

127.0.0.1:5432
```

