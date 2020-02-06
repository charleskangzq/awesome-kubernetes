# 简单服务上Kubernetes平台流程

## 服务开发

|	项目类型   |	开发团队工作			|
|--------------|----------------------------|
|开源项目	   |		无					|
|自研项目	   |开发团队需要进行开发工作	|

## 服务部署

### 镜像打包

开发人员将服务开发完成后打包成镜像，将镜像上传到镜像仓库：XXXXXXXXXX

### Chart开发

#### chart结构

```
.
└── redis
    ├── backup
    │   ├── chart.yaml
    │   ├── template
    │   └── values.yaml
    └── deploy
        ├── chart.yaml
        ├── template
        └── values.yaml
```

2. 将开发完成的Chart包上传到Chart仓库：XXXXXXXXXXX

## 服务运维

详细参考[服务运维](./service-operations-on-kubernetes.md)

## 服务监控

详细参考[服务监控](./service-metric-on-kubernetes.md)