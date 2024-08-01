# Setting Up MySQL with Docker on Kali Linux

This guide will walk you through the process of setting up a MySQL server using Docker on Kali Linux. This method ensures that the MySQL installation does not interfere with your system's packages and dependencies.

## Step 1: Install Docker

First, ensure Docker is installed on your system:

```

sudo apt update
sudo apt install docker.io

```
```
sudo systemctl start docker
sudo systemctl enable docker
docker pull mysql:latest
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=my-secret-pw -p 3306:3306 -d mysql:latest
docker exec -it mysql-container mysql -u root -p
docker stop mysql-container
docker start mysql-container
docker rm mysql-container
docker logs mysql-container


# docker compose file
version: '3.1'

services:
  db:
    image: mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
    ports:
      - "3306:3306"

```
