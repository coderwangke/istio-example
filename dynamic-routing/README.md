# dynamic routing

根据请求的user字段，修改请求的访问的版本

### 前提

- 已经部署好bookinfo应用，并且可以访问
- 已经设置static-routing规则，所有流量都指向服务的v1版本

### 部署

设置规则，使得用户`jason`访问`reviews:v2`版本，其他用户方为v1版本

```
kubectl apply -f dynamic-routing/virtual-service-reviews-test-v2.yml
```

### 验证

登录jason（不需要密码）访问v2版本，可以看到黑色星星，不登录或者使用其他用户则访问v1版本，无星星
