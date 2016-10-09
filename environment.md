# 環境設定

## 使用 MariaDB docker image
- [library/mariadb - Docker Hub](https://hub.docker.com/_/mariadb/)

### 下載 Image
```shell
$ docker pull mariadb
```

### 啟動 Container
```shell
$ docker run --name db -e MYSQL_ROOT_PASSWORD=111111 -d mariadb
```

### 進入 Container
```shell
$ docker exec -it db bash
root@d1efd31f01f8:/#
```

### 進入 MariaDB
```shell
root@d1efd31f01f8:/# mysql -uroot -p111111
MariaDB [(none)]>
```

### 離開 MariaDB
```shell
MariaDB [(none)]> quit
Bye
```

### 離開 Container
```shell
root@d1efd31f01f8:/# exit
$
```

### 停止/刪除 Container
```shell
$ docker stop db
$ docker rm db
```
