## 1. 🐬 PHP My Admin Docker Connect with MySQL Docker
```sh
docker run -d \
  --name phpmyadmin-container \
  --link mysql-container:db \
  -p 8080:80 \
  phpmyadmin
```
