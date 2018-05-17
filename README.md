# Dockerized Symfony-4 Container

### What's included?
* PHP 7.2
* MySQL
* NginX

### How to install?
```
$ cd DockerizedSymfony4
$ docker-compose build
$ docker-compose up -d
```

### List all running containers
```
$ docker ps

CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                     NAMES
bbdfe4be67b3        stta_nginx          "nginx -g 'daemon of…"   12 days ago         Up 25 minutes       0.0.0.0:8080->80/tcp      stta_nginx_1
4664f8c84678        stta_php            "docker-php-entrypoi…"   12 days ago         Up 25 minutes       0.0.0.0:9000->9000/tcp    stta_php_1
1966368c0126        mysql               "docker-entrypoint.s…"   12 days ago         Up 25 minutes       0.0.0.0:33060->3306/tcp   stta_mysql_1
```

### Create Symfony4 project
```
$ docker exec -it stta_php_1 bash
$ cd /var/www
$ composer create-project symfony/skeleton my_project
```