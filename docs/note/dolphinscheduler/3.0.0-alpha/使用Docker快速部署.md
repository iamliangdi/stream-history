# 使用Docker快速部署

> 作者：梁帝

## 1 Docker-Compose和Docker-Swarm部署方式

> 使用 docker-compose 启动服务的优点是 DolphinScheduler 的各个是独立的容器和进程，相互影响降到最小，且能够在 服务重启的时候保留元数据（如需要挂载到本地路径需要做指定）。

### 1.1 部署流程

#### 1.1.1 使用Docker-Compose文件，相关命令如下

```shell
# 以容器方式启动
docker-compsoe up -d
# 查看当前正在运行的容器
docker ps
# 查看LOGS
docker logs ${containerId} 
# 停止运行并删除容器
docker-compose stop
# 停止运行并删除容器和数据卷
docker-compose stop -v
```

#### 1.1.2 使用Docker-Swarm文件，相关命令如下

```shell
# 以stack方式启动
docker stack deploy -c docker-stack.yml dolphinscheduler
# 查看当前运行的stack
docker stack ls
# 查看当前运行的service
docker service ls
# 停止并移除stack
docker stack rm dolphinscheduler
```

### 1.2 Docker-Compose文件配置详解

> 查看[docker-compose.yml文件](docker/docker-compose.yml)

#### 1.2.1 必须依赖组件

* postgresql/mysql：提供数据持久化
* zookeeper：服务发现

#### 1.2.2 核心组件

* api：web应用模块，提供ApiService
* master：主节点
* worker：工作节点
* alert-server：告警服务（非必须）
* schema-initializer：库表初始化（可能遇到依赖删除问题，建议使用[POSTGRESQL](init_sql/dolphinscheduler_postgresql.sql)
  /[MYSQL](init_sql/dolphinscheduler_mysql.sql)/[H2](init_sql/dolphinscheduler_h2.sql)文件自行执行）

### 1.3 访问项目

> 访问http://${部署IP}:12345/dolphinscheduler/
>
> 登录账号：admin
>
> 登录密码：dolphinscheduler123


