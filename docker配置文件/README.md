参考 [Docker官方配置文档](https://docs.docker.com/engine/reference/commandline/dockerd/#/configuration-reloading)，修改/etc/docker/daemon.json

```json
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
    
  // docker数据目录
  "data-root": "/var/lib/docker",
  "experimental": false,
  "features": {
    "buildkit": true
  },
  
  // 私有Registry地址
  "insecure-registries": [
      
  ],
    
  // 镜像加速地址
  "registry-mirrors": [
    "https://registry.docker-cn.com",
    "https://registry.cn-hangzhou.aliyuncs.com",
    "https://mirror.ccs.tencentyun.com"
  ]
}
```
