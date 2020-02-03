# Kubernetes Operator开发流程

## Operator开发

使用[Operator-SDK](https://github.com/operator-framework/operator-sdk)工具辅助整个Operator的开发

1. 生成项目

```
$ operator-sdk new app-operator
```

2. 添加CRD资源类型

```
$ operator-sdk add api --api-version=app.example.com/v1alpha1 --kind=AppService
```

3. 添加CRD资源Controller

```
$ operator-sdk add controller --api-version=app.example.com/v1alpha1 --kind=AppService
```

4. 最终项目目录结构

```
```


## Operator部署

### 镜像打包


### Chart开发


## Operator运维

1. 开发自己服务独有运维工具

## Operator监控

1. 日志

2. UI
