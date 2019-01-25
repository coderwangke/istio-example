# denial

实现简单的请求拒绝

### 前提

- 已经部署好bookinfo应用，并且可以访问
- 已经设置static-routing规则，所有流量都指向服务的v1版本

### 部署

首先，设置规则，使得用户jason访问`reviews:v2`版本，其他用户和不登录用户访问`reviews:v3`版本

```
kubectl apply -f policy/denial/virtual-service-reviews-jason-v2-v3.yml
```

接下来，设置deny规则，拒绝`reviews:v3`版本的请求

```
kubectl apply -f policy/denial/mixer-rule-deny-label.yaml
```


### 验证
返回浏览器，访问`http://EXTERNAL-IP/productpage`，使用jason用户的其他用户登录将看不到任何`rating`的星星，应为v3版本被设置为拒绝访问`rating`服务.
