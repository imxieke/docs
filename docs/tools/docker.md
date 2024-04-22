# Docker


## Dockerd
```conf
[Service]
Environment="HTTP_PROXY=http://192.168.13.189:7890"
Environment="HTTPS_PROXY=http://192.168.13.189:7890"
Environment="NO_PROXY=localhost,127.0.0.1,.example.com"
```

## Container
## ~/.docker/config.json

```json
{
 "proxies":
 {
   "default":
   {
     "httpProxy": "http://192.168.13.189:7890",
     "httpsProxy": "http://192.168.13.189:7890",
     "noProxy": "localhost,127.0.0.1,.example.com"
   }
 }
```

## Build
``` bash
docker build . \
    --build-arg "HTTP_PROXY=http://proxy.example.com:8080/" \
    --build-arg "HTTPS_PROXY=http://proxy.example.com:8080/" \
    --build-arg "NO_PROXY=localhost,127.0.0.1,.example.com" \
    -t your/image:tag
```

```bash
sudo systemctl daemon-reload
sudo systemctl restart docker
```

## Set Mirrors
### 检查 `docker.service` 是否已经配置
`systemctl cat docker | grep '\--registry-mirror'`

使用下面命令编辑配置文件
`nvim /etc/docker/daemon.json`

``` json
{
  "registry-mirrors": [
    "https://hub-mirror.c.163.com",
    "https://mirror.baidubce.com"
  ]
}
```

重启 `docker` 完成配置, 可通过 `docker info` 查看是否配置成功

`sudo systemctl restart docker`

## Config Proxy
```shell
mkdir -p /etc/systemd/system/docker.service.d
nvim /etc/systemd/system/docker.service.d/proxy.conf
[Service]
Environment="HTTP_PROXY=http://192.168.2.147:7890"
Environment="HTTPS_PROXY=http://192.168.2.147:7890"
Environment="NO_PROXY="localhost,127.0.0.1,::1"

## 重启后生效
sudo systemctl daemon-reload
sudo systemctl restart docker
```

## 非 `root` 用户运行
```
将当前用户添加到 docker 组
sudo usermod -aG docker $USER
刷新群组
newgrp - docker
```

## Third Registry
- Tencent
    - hkccr.ccs.tencentyun.com 891788135:ke19960318

##  Search Third Registry
docker search registry.access.redhat.com/rhel rhel 是镜像名称
quay.io/ubuntu

```
docker commit imagesID imagesName -m='commit content' -a='Xiekers'
docker build -t user/images .  Dockerfile location Directory
docker push imxieke/images:tag
```


Refer link: http://www.tuicool.com/articles/e2YrE3j

## Command list
>Command list and introduction

 1. FROM        指定Container base image 来源
 2. MAINTAINER: 维护者&作者<MAINTAINER Mail>
 3. RUN         Linux Command
 4. ENV         设置环境变量。
 5. EXPOSE      暴露端口
 6. ADD         添加文件至Container内
 7. COPY        复制本地主机的 <src> （为Dockerfile所在目录的相对路径）到容器中的 <dest>
 8. VOLUME      挂载Volume 持久化存储文件
 9. ENTRYPOINT  Dockerfile仅可指定一个ENTRYPOINT，若指定多个，仅一个有效
 10. CMD         镜像构建容器后被调用。
 11. WORKDIR    WORKDIR命令用于设置CMD指明的命令的运行目录。
 12. ONBUILD    配置当所创建的镜像作为其它新创建镜像的基础镜像时，所执行的操作指令。


PS:RUN先于CMD/ENTRYPOINTRUN命令覆盖CMD
例：CMD["echo"] 而docker run CONTAINER_NAME echo foo则会运行echo foo，
而忽略CMD 而ENTRYPOINT则会传递RUN命令，
例：ENTRYPOINT ["echo"]docker run CONTAINER_NAME echo foo则会运行echo echo foo 输出为echo foo

*****************************************************************


>Introduction Command  usage and example;
### FROM

    用法：ubuntu/xenial:tag (daocloud.io/library:ubuntu or tag)

### MAINTAINER

    # Usage: MAINTAINER [name]
    MAINTAINER Xiekers <im@xieke.org>

## ENV

    #usage:ENV KEY Volue
    ENV PHP 5.5
    用于设置环境变更
    使用此dockerfile生成的image新建container，可以通过 docker inspect CONTAINER ID  看到这个环境变量
    也可以通过在docker run时设置或修改环境变量
    指定一个环境变量，会被后续 RUN 指令使用，并在容器运行时保持。
    ###Example###
    ENV PG_MAJOR 9.3
    ENV PG_VERSION 9.3.4
    RUN curl -SL http://example.com/postgres-$PG_VERSION.tar.xz | tar -xJC /usr/src/postgress && …
    ENV PATH /usr/local/postgres-$PG_MAJOR/bin:$PATH

### ADD

    #Usage ADD <src> <dest>
    ADD index.php /var/www/html
    ADD http://xxx.xxx/xxx.zip /var/www/html    //会被下载并复制到Container
    ADD package.zip /var/www/html                 //会被解压出来


### COPY

    #usage COPY src /destination
    COPY index.php /var/www/html



### USER

    比如指定 memcached 的运行用户，可以使用上面的 ENTRYPOINT or CMD来实现:
    ENTRYPOINT ["memcached", "-u", "daemon"]
    更好的方式：
    ENTRYPOINT ["memcached"]
    USER daemon

## VOLUME

    #usage VOLUME ["<mountpoint>"]
    如:`VOLUME ["/data"]`
    创建一个挂载点用于共享目录

## WORKDIR

    #usage WORKDIR /path/to/workdir
    配置RUN, CMD, ENTRYPOINT 命令设置当前工作路径
    可以设置多次，如果是相对路径，则相对前一个 WORKDIR 命令
    比如:`WORKDIR /a WORKDIR b WORKDIR c RUN pwd`
    其实是在 /a/b/c 下执行 pwd

### USER

    比如指定 memcached 的运行用户，可以使用上面的 ENTRYPOINT or CMD来实现:
    ENTRYPOINT ["memcached", "-u", "daemon"]
    更好的方式：
    ENTRYPOINT ["memcached"]
    USER daemon
    SER命令用于设置运行容器的UID。
    # Usage: USER [UID]
    USER 751

### EXPOSE

    #Usage EXPOSEd <port>
    在docker使用--link来链接两容器时会用到相关端口


### CMD

    和RUN命令相似，CMD可以用于执行特定的命令。和RUN不同的是，这些命令不是在镜像构建的过程中执行的，而是在用镜像构建容器后被调用。支持三种格式

    CMD ["executable","param1","param2"] 使用 exec 执行，推荐方式；
    CMD command param1 param2 在 /bin/sh 中执行，提供给需要交互的应用；
    CMD ["param1","param2"] 提供给 ENTRYPOINT 的默认参数；

    #Usage 1: CMD application "argument", "argument", ..
    CMD "echo" "Hello docker!"


### ONBUILD

    #usage:ONBUILD [INSTRUCTION]
    #用途：配置当所创建的镜像作为其它新创建镜像的基础镜像时，所执行的操作指令。
    例如，Dockerfile使用如下的内容创建了镜像 image-A 。
    ONBUILD ADD . /app/src
    ONBUILD RUN /usr/local/bin/python-build --dir /app/src
    如果基于A创建新的镜像时，新的Dockerfile中使用 FROM image-A 指定基础镜像时，会自动执行 ONBUILD 指令内容，等价于在后面添加了两条指令。
    FROM image-A
    #Automatically run the following
    ADD . /app/src
    RUN /usr/local/bin/python-build --dir /app/src
    使用 ONBUILD 指令的镜像，推荐在标签中注明，例如 ruby:1.9-onbuild 。

# Dockerfile Example
```

    FROM centos6-base
    MAINTAINER Xiekers <im@xieke.org>
    RUN ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key
    RUN ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key
    RUN sed -ri 's/session    required     pam_loginuid.so/#session    required     pam_loginuid.so/g' /etc/pam.d/sshd
    RUN mkdir -p /root/.ssh && chown root.root /root && chmod 700 /root/.ssh
    EXPOSE 22
    RUN echo 'root:redhat' | chpasswd
    RUN yum install -y yum-priorities && rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm && rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6
    RUN yum install tar gzip gcc vim wget -y
    ENV LANG en_US.UTF-8
    ENV LC_ALL en_US.UTF-8
    CMD /usr/sbin/sshd -D
    #End

```

    FROM       php
    MAINTAINER Xiekers <im@xieke.org>
    #将index.php复制到容器内的/var/www目录下
    ADD        index.php /var/www/
    #对外暴露8080端口
    EXPOSE     8080
    #设置Volume挂载目录
    VOLUME ["/data"]
    # 设置容器默认工作目录为/var/www
    WORKDIR    /var/www/
    # 容器运行后默认执行的指令
    ENTRYPOINT ["php", "-S", "0.0.0.0:8080"]
    CMD service tomcat7 start                     #无效命令运行几秒钟之后，容器就会退出
    ENTRYPOINT service tomcat7 start       #无效命令运行几秒钟之后，容器就会退出
    #正确写法 CMD相同
    ENTRYPOINT service tomcat7 start && tail -f /var/lib/tomcat7/logs/catalina.out
    OR
    ENTRYPOINT ["/usr/sbin/sshd"]
    CMD ["-D"]

### Docker

`apk add --no-cache` 不使用本地缓存安装包数据库，直接从远程获取安装包信息安装。这样我们就不必通过apk update获取安装包数据库了

`apk add --virtual .build-deps` 将本次安装的所有包封装成一个名为.build-deps的虚拟包。这样做的好处是可以通过apk del .build-deps一键清除这些包

## Docker 运行实例
``` shell
docker run -d\
	--name mariadb \
	-v /Volumes/MacData/Code/Devenv/Volumes/mariadb:/var/lib/mysql \
	-e MYSQL_ROOT_PASSWORD=19960318 \
	-p 3306:3306 \
	mariadb:10.3.8

docker run -it \
	--link some-mariadb:mysql \
	--rm mariadb sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'
```

## error: failed to initialize alpm library
> apt-get install runc

## GPU
```shell
[ "$GPU_TYPE" = NVIDIA ] && GPU_DEVICE_PARAMETERS="--device=/dev/nvidiactl --device=/dev/nvidia-uvm --device=/dev/nvidia0"
[ "$GPU_TYPE" = INTEL ] && GPU_DEVICE_PARAMETERS="--device=/dev/dri:/dev/dri"
```