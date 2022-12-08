# docker操作记录

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
```