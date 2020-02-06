# 复杂状态服务上Kubernetes平台流程

## 服务开发

|   项目类型   |    开发团队工作          |
|--------------|----------------------------|
|开源项目      |        无                   |
|自研项目      |开发团队需要进行开发工作    |

## 服务部署

### Operator开发

使用[Operator-SDK](https://github.com/operator-framework/operator-sdk)工具辅助整个Operator的开发，以Redis服务为示例

#### 生成项目

```
$ operator-sdk new redis-operator
```

#### 添加CRD

```
$ operator-sdk add api --api-version=jdcloud.com/v1alpha1 --kind=RedisCluster
```

#### 添加Controller

```
$ operator-sdk add controller --api-version=jdcloud.com/v1alpha1 --kind=RedisCluster
```

#### 项目初始化后目录结构

```
redis-operator/
├── build
│   ├── bin
│   │   ├── entrypoint
│   │   └── user_setup
│   └── Dockerfile
├── cmd
│   └── manager
│       └── main.go
├── deploy
│   ├── crds
│   │   ├── jdcloud.com_redisclusters_crd.yaml
│   │   └── jdcloud.com_v1alpha1_rediscluster_cr.yaml
│   ├── operator.yaml
│   ├── role_binding.yaml
│   ├── role.yaml
│   └── service_account.yaml
├── go.mod
├── go.sum
├── pkg
│   ├── apis
│   │   ├── addtoscheme_jdcloud_v1alpha1.go
│   │   ├── apis.go
│   │   └── jdcloud
│   │       ├── group.go
│   │       └── v1alpha1
│   │           ├── doc.go
│   │           ├── rediscluster_types.go
│   │           ├── register.go
│   │           └── zz_generated.deepcopy.go
│   └── controller
│       ├── add_rediscluster.go
│       ├── controller.go
│       └── rediscluster
│           └── rediscluster_controller.go
├── tools.go
└── version
    └── version.go
```

#### 开发服务自身逻辑

服务定义：开发人员在pkg/apis/jdcloud/v1alpha1/rediscluster_types.go文件里面添加管理服务需要的字段

服务逻辑：开发人员在pkg/controller/rediscluster/rediscluster_controller.go文件里面添加管理服务需要的逻辑

### Operator测试

TODO

### Operator部署


### Operator运维

1. 开发自己服务独有运维工具

### Operator监控

TODO

## 服务运维

详细参考[服务运维](./service-operations-on-kubernetes.md)

## 服务监控

详细参考[服务监控](./service-metric-on-kubernetes.md)