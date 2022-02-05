# 虚拟机安装Ubuntu

## 一、基础配置

- 设置镜像，以阿里云镜像为例

> http://mirrors.aliyun.com/ubuntu/

- 设置root账户

```shell
> set passwd root
```

- 允许远程登录 Root

```shell
# 编辑文件
> vim /etc/ssh/sshd_config 
# 注释此行
#PermitRootLogin without-password  
# 加入此行
PermitRootLogin yes 

# 重启服务
> service ssh restart
```

- 修改主机名

```shell
# 防止hostname还原
> vi /etc/cloud/cloud.cfg

# 该配置默认为 false，修改为 true 即可
preserve_hostname: true

# 修改主机名
> hostnamectl set-hostname develop

# 配置 hosts 加入地址（可忽略）
cat >> /etc/hosts << EOF
192.168.xx.xx develop
EOF
```

- 修改IP

```shell
# 编辑配置文件
> vi /etc/netplan/50-cloud-init.yaml
# 文件内容如下
network:
    ethernets:
        ens33:
          # ip地址
          addresses: [192.168.xx.xx/24]
          # 网关地址
          gateway4: 192.168.xx.x
          # 对外部域名
          nameservers:
            addresses: [192.168.xx.x]
          # 动态主机配置协议，为true时会保留自动生成的ip
          dpch4: false
    version: 2
# 重启服务生效
> netplan apply
```

- 修改DNS,否则可能无法上网

```shell
# 取消DNS行注释，并增加 DNS 配置如：114.114.114.114，修改后重启
> vim /etc/systemd/resolved.conf
```