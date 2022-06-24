# docker的安装

### 1. Ubuntu系统

- 卸载旧版本

```shell
> apt-get remove docker docker-engine docker.io containerd runc
```

- 更新包索引

```shell
> apt-get update
```

- 使用apt安装

```shell
> apt install docker.io
```

- 验证

```shell
> docker version
```

- 配置镜像加速器(阿里云获取)

```shell
> vi /etc/docker/daemon.json
# 写入内容
{
  "registry-mirrors": ["https://xxxxxxxx.mirror.aliyuncs.com"]
}
```

- 重启docker

```shell
> systemctl daemon-reload
> systemctl restart docker
```

- 验证

```shell
> docker info
```