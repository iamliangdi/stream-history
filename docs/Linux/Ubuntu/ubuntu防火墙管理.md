# Ubuntu防火墙管理

- 安装防火墙(一般自带)

```shell
> sudo apt-get install ufw
```

- 查看防火墙状态

```shell
> sudo ufw status
```

- 启用(开机自动启动)和关闭(开机不启动)防火墙

```shell
> sudo ufw enable
> sudo ufw disable
```

- 默认打开或关闭所有端口

```shell
> sudo ufw default allow
> sudo ufw default deny
```

- 打开或关闭某个端口(服务)

```shell
> sudo ufw allow smtp
> sudo ufw allow 80
> sudo ufw allow 22/tcp
> sudo ufw deny smtp
> sudo ufw deny 80
> sudo ufw deny 22/tcp
```

- 指定ip访问

```shell
> sudo ufw allow from 192.168.1.1
> sudo ufw allow from 192.168.1.1 to any port 22
```

- 删除规则

```shell
> sudo ufw delete allow 80
```

- 重启防火墙

```shell
> sudo ufw reload
```