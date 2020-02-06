# 上传Chart包流程



### Chart仓库

使用京东云对象存储（OSS）作为 Chart 仓库
仓库URL：chart-repo-donot-delete.s3.cn-south-1.jdcloud-oss.com



### 本地添加私有仓库

`helm repo add [私有仓库本地别名] http://chart-repo-donot-delete.s3.cn-south-1.jdcloud-oss.com`

```
helm repo add repo-jdcloud http://chart-repo-donot-delete.s3.cn-south-1.jdcloud-oss.com
"repo-jdcloud" has been added to your repositories
```



执行`helm repo list  `验证是否添加成功

```
root@k8s-client:~/chart# helm repo list
NAME            URL
repo-jdcloud    http://chart-repo-donot-delete.s3.cn-south-1.jdcloud-oss.com
```



### 生成待上传的Chart包

1.使用```helm package [chart PATH]```命令生成.tgz文件


```
root@k8s-client:~/chart# helm package mychart/
Successfully packaged chart and saved it to: /root/chart/mychart-0.1.0.tgz
```

```
root@k8s-client:~/chart# ls
mychart  mychart-0.1.0.tgz
```



2.使用```helm repo index [.tgz文件所在path]```命令生成新index.yaml文件

```
root@k8s-client:~/chart# helm repo index ./
root@k8s-client:~/chart# ls
index.yaml  mychart  mychart-0.1.0.tgz
```



3.将index.yaml文件与.tgz文件上传到oss中

使用控制台或者api上传到chart-repo-donot-delete.s3.cn-south-1.jdcloud-oss.com


