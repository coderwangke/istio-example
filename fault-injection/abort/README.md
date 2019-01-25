# abort

根据请求的user字段，拒绝特定用户访问服务

### 前提

- 已经部署好bookinfo应用，并且可以访问
- 已经设置dynamic-routing规则，除了用户jason访问reviews的v2版本，其他用户访问v1版本

### 部署

设置规则，针对用户设置HTTP中止故障

```
kubectl apply -f fault-injection/abort/virtual-service-ratings-test-abort.yml
```

### 验证

返回浏览器，访问`http://EXTERNAL-IP/productpage`，登录用户jason，页面显示产品评级不可用消息
