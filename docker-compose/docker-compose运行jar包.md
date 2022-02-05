# docker-compose运行jar包

- 编辑Dockerfile文件如下

```dockerfile
FROM openjdk
#复制当前jar到容器根目录下
ADD ./xxxxx.jar xxxxx.jar
#复制配置文件到根目录下
COPY ./config/application.yml /
# 运行该jar
CMD java -jar xxxxx.jar --spring.config.location=/application.yml > /log/start.log
```

- 编辑docker-compose.yml文件如下

```yaml
version: '3.8'
services:
  xxxxx:
    image: liangdi/xxxxx
    build: ../docker
    container_name: xxxxx
    volumes:
      - ./logs:/log
```