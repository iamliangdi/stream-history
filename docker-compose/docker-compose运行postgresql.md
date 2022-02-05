# docker-compose运行postgresql

- docker-compose.yml文件如下

```yaml
version: '3.8'
services:
  postgresql:
    image: postgres
    container_name: postgresql
    privileged: true
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: root
      POSTGRES_PASSWORD: 123456
    volumes:
      - ./data:/var/lib/postgresql/data
```