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

sudo apt install docker-compose



version: '3.8'

services:
  mysql:
    image: mysql:latest
    container_name: mysql-container
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw  # Set the root password
      MYSQL_DATABASE: mydatabase         # Create a default database
      MYSQL_USER: myuser                 # Optional: Set a default user
      MYSQL_PASSWORD: myuserpassword     # Optional: Set a default user password
    ports:
      - "3306:3306"                      # Map port 3306 of the container to port 3306 on the host
    volumes:
      - mydbdata:/var/lib/mysql          # Persist data even if the container stops
    restart: always

volumes:
  mydbdata:                              # Defines the volume

docker-compose up -d
docker-compose ps
docker exec -it mysql-container mysql -u root -p


```
