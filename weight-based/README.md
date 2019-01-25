# weight-based routing

实现服务请求的权重比例的分配

### 前提

- 已经部署好bookinfo应用，并且可以访问
- 已经设置static-routing规则，所有流量都指向服务的v1版本

### 部署


设置规则，实现50%的流量都转到v1版本，50%的流量转到v3版本

```
kubectl apply -f weight-based/virtual-service-reviews-50-v3.yml
```

### 验证
返回浏览器，访问`http://EXTERNAL-IP/productpage`，刷新多次，大约有50%的机会看到红色星星