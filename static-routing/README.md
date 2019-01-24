# static routing

### 前提

- 已经部署好bookinfo应用，并且可以访问
- 已经设置static-routing规则，所有流量都指向服务的v1版本

### 部署

首先，设置destination-rule

```
kubectl apply -f static-routing/destination-rule-all-mtls.yml
```

接下来，设置规则，所有的流量都转到服务的v1版本

```
kubectl apply -f static-routing/virtual-service-all-v1.yml
```

查看virtualservice:

```
kubectl get virtualservices
```

### 验证
返回浏览器，访问`http://EXTERNAL-IP/productpage`，刷新几次，查看是否可以看到星星。因为`reviews:v1`不会访问`rating`服务。

