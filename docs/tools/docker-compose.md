# 

```YML
version: '2'
services:
    redis:
        image: redis:alpine
        ports:
          - 6379:6379
        networks:
          - frontend
        deploy:
          replicas: 2
          update_config:    # 配置如何更新服务
            parallelism: 2  # 每次要更新的容器数量
            delay: 10s  # 更新下一组容器前要等待的时间
                resources:
            limits:
              cpus: "0.1"
              memory: 50M
        restart_policy:
          condition: on-failure
          max_attempts: 3
          delay: 10s
    sb2:
        restart: always
        build:
        context: .
        ports:
          - 8002:8080
    sb3:
        restart: always
        build:
        context: .
        ports:
          - 8003:8080
    mysql:
        network_mode: "bridge"
        environment:
            MYSQL_ROOT_PASSWORD: "111111"
            MYSQL_USER: 'test'
            MYSQL_PASS: '111111'
        image: "mysql:latest"
        restart: always
        volumes:
            - "./db:/var/lib/mysql"
            - "./conf/my.cnf:/etc/my.cnf"
            - "./init:/docker-entrypoint-initdb.d/"
        ports:
            - "33060:3306"

networks:
  frontend:
  backend:

volumes:
  db-data:
```