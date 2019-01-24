# static routing

### 前提

- 已经部署好bookinfo应用，并且可以访问
- 已经设置static-routing规则，所有流量都指向服务的v1版本

### 部署

首先，设置规则，为`rating`注入2s的延迟

```
kubectl apply -f fault-injection/timeout/virtual-service-test-2s-delay.yml
```

接下来，设置规则，为`reviews:v2`设置1s超时

```
kubectl apply -f fault-injection/timeout/virtual-service-test-1s-timeout.yml
```

### 验证
