# 🔧 Dockerized Multi-Database Setup Guide

This guide walks you through running **MongoDB**, **Microsoft SQL Server**, **MySQL**, **Oracle**, **PostgreSQL**, and **Redis** containers using Docker, with persistent storage and proper user credentials.

---

## 1. 🚀 MongoDB

```bash
docker run -d \
  --name mongo-container \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=nopass \
  -v mongodata:/data/db \
  -p 27017:27017 \
  mongo
```

**Credentials:**

* Username: `admin`
* Password: `nopass`

---

## 2. 🧩 Microsoft SQL Server (MSSQL)

```bash
docker run -d \
  --name mssql-container \
  -e ACCEPT_EULA=Y \
  -e SA_PASSWORD=Nopass#123 \
  -v mssqldata:/var/opt/mssql \
  -p 1433:1433 \
  mcr.microsoft.com/mssql/server:2022-latest
```

**Credentials:**

* Username: `sa`
* Password: `Nopass#123`

---

## 3. 🐬 MySQL

```bash
docker run -d \
  --name mysql-container \
  -e MYSQL_ROOT_PASSWORD=nopass \
  -e TZ=Asia/Dhaka \
  -v mysql-data:/var/lib/mysql \
  -v /etc/timezone:/etc/timezone:ro \
  -v /etc/localtime:/etc/localtime:ro \
  -p 3306:3306 \
  mysql
```

**Credentials:**

* Username: `root`
* Password: `nopass`

---

## 4. 🏛 Oracle Database (Free Edition)

```bash
docker run -d \
  --name oracle-free \
  -p 1521:1521 \
  -e ORACLE_PASSWORD='Nopass#123' \
  -v oracle-data:/opt/oracle/oradata \
  gvenzl/oracle-free:latest-faststart
```

**DataGrip Configuration:**

* Connection Type: `Service`
* Service Name: `FREEPDB1`
* Username: `system`
* Password: `Nopass#123`

---

## 5. 🐘 PostgreSQL

```bash
docker run -d \
  --name postgres-container \
  -e POSTGRES_USER=postgres \
  -e POSTGRES_PASSWORD=nopass \
  -e POSTGRES_DB=postdb \
  -v pgdata:/var/lib/postgresql/data \
  -p 5432:5432 \
  postgres
```

**Credentials:**

* Username: `postgres`
* Password: `nopass`
* Database: `postdb`

---

## 6. 🔴 Redis (Persistent Storage Enabled)

```bash
docker run -d \
  --name redis-container \
  -v redisdata:/data \
  -p 6379:6379 \
  redis \
  redis-server --appendonly yes
```

**No password set by default.**
Data is persisted using AOF (`appendonly yes`).

---

## 📝 Notes:

* All data is persisted using Docker volumes (e.g., `mongodata`, `mssqldata`, etc.).
* All services are exposed to localhost with standard default ports.
* You can inspect volumes using: `docker volume ls`

---
