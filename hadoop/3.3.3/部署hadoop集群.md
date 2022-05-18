# Hadoop集群部署

> 作者：梁帝

## 1 准备环境

 - 三台服务器（虚拟机）
 - 设置每台服务器的`/etc/hosts`文件，能够识别hostname即可
 - 服务器已配置[JDK](https://www.oracle.com/java/technologies/downloads/环境)环境

## 2 在master服务器下载并解压hadoop

```shell
# 下载HADOOP至/data目录，目录是自定义的，我习惯使用此路径
wget https://mirrors.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-3.3.3/hadoop-3.3.3.tar.gz /data
# 解压hadoop
cd /data
tar -zxvf hadoop-3.3.3.tar.gz
# 将文件分别发送至两台slave服务器，[***]是命令待替换的内容
scp ./hadoop-3.3.3.tar.gz [用户名]@[服务器hostname]:[发送路径]
# 发送完成后在两台slave服务器上分别执行解压hadoop的步骤
```

