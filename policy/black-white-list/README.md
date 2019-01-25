# blacklist/whitelist

实现黑白名单限制

### 前提

- 已经部署好bookinfo应用，并且可以访问
- 已经设置static-routing规则，所有流量都指向服务的v1版本

### 部署

首先，设置规则，使得用户jason访问`reviews:v2`版本，其他用户和不登录用户访问`reviews:v3`版本

```
kubectl apply -f policy/denial/virtual-service-reviews-jason-v2-v3.yml
```

接下来，设置黑白名单限制，将`reviews:v3`置于黑名单中，即不允许`reviews:v3`版本服务访问ratings服务

```
kubectl apply -f policy/denial/mixer-rule-black-white-list.yml
```


### 验证
返回浏览器，访问`http://EXTERNAL-IP/productpage`，使用jason用户登录可以看到星星，不登录则看不到星星.
