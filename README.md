# docker操作记录

## 不加sudo执行docker

```
$ 不加 sudo 执行 Docker 命令
```

## docker删除无用镜像

```
$ docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
```
## docker-compose启动zookeeper和kafka

```
// 设置docker虚拟网络
$ docker network create --driver bridge --subnet 172.23.0.0/25 --gateway 172.23.0.1  network01

$ cd zookeeper
$ docker-compose up -d

$ cd ../kafka
$ docker-compose up -d
```

## docker启动clickhouse

```
$ docker run -d --name ch-server --ulimit nofile=262144:262144 -p 9000:9000 -p 8123:8123 -v /etc/timezone:/etc/timezone -v /etc/localtime:/etc/localtime yandex/clickhouse-server
```

## docker启动mysql

```
$ docker run -d -p 3306:3306 --name mysql --restart=always -v /var/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 mysql:5.7
```

## docker启动redis

```
$ docker run -d -p 6379:6379 --name redis --restart=always redis

// 设置密码
$ docker run -d --name myredis -p 6379:6379 redis --requirepass "mypassword"
```

## docker启动gitlab

```
docker run --detach \
  --hostname gitlab.demo.com \
  --publish 8443:443 --publish 8880:80 --publish 8222:22 \
  --name gitlab \
  --restart always \
  --volume /srv/gitlab/config:/etc/gitlab \
  --volume /srv/gitlab/logs:/var/log/gitlab \
  --volume /srv/gitlab/data:/var/opt/gitlab \
  gitlab/gitlab-ce:latest
```
