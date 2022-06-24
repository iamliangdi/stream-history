# docker-compose的安装

1、 下载文件，注意版本号可在链接中修改

> [查看docker-compose版本](https://github.com/docker/compose/releases)

```shell
wget https://github.com/docker/compose/releases/download/1.28.0/docker-compose-$(uname -s)-$(uname -m) -O /usr/local/bin/docker-compose
```

2、 添加执行权限

```shell
sudo chmod +x /usr/local/bin/docker-compose
```

3、验证

```shell
docker-compose --version
```