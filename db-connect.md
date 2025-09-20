## 1. 🐬 PHP My Admin Docker Connect with MySQL Docker (Modern Way)

```sh
docker network create mynet

docker run -d \
  --name mysql-container \
  --network mynet \
  -e MYSQL_ROOT_PASSWORD=nopass \
  -e TZ=Asia/Dhaka \
  -v mysql-data:/var/lib/mysql \
  -v /etc/timezone:/etc/timezone:ro \
  -v /etc/localtime:/etc/localtime:ro \
  -p 3306:3306 \
  mysql

docker run -d \
  --name phpmyadmin-container \
  --network mynet \
  -e PMA_HOST=mysql-container \
  -p 8080:80 \
  phpmyadmin
```
