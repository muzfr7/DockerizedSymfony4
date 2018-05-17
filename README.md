# Dockerized Symfony4
Docker containers configured and ready to start developing traditional web application, microservice, console application or an API..

### What's included?
* PHP 7.2
* MySQL
* NginX

### How to install?
**Step 1.** Having [Git](https://git-scm.com) installed, clone this repository somewhere in your computer, for this example I'm going to clone it in `~/Developer/` directory:
```
$ cd ~/Developer
$ git clone https://github.com/muzfr7/DockerizedSymfony4.git
```

**Step 2.** You may want to update timezone settings in following files:
```
$ nano DockerizedSymfony4/nginx/Dockerfile
$ nano DockerizedSymfony4/php-fpm/Dockerfile
$ nano DockerizedSymfony4/php-fpm/php.ini
```

**Step 3.** Having [Docker](https://www.docker.com) natively installed on your computer, build and run containers:
```
$ cd ~/Developer/DockerizedSymfony4
$ docker-compose build
$ docker-compose up -d
```

### List all running containers
```
$ docker ps

CONTAINER ID        IMAGE                       COMMAND                  CREATED             STATUS              PORTS                     NAMES
bbdfe4be67b3        dockerizedsymfony4_nginx    "nginx -g 'daemon of…"   1 hour ago         Up 25 minutes       0.0.0.0:8080->80/tcp      dockerizedsymfony4_nginx_1
4664f8c84678        dockerizedsymfony4_php      "docker-php-entrypoi…"   1 hour ago         Up 25 minutes       0.0.0.0:9000->9000/tcp    dockerizedsymfony4_php_1
1966368c0126        mysql                       "docker-entrypoint.s…"   1 hour ago         Up 25 minutes       0.0.0.0:33060->3306/tcp   dockerizedsymfony4_mysql_1
```

### Create Symfony4 project
```
$ docker exec -it dockerizedsymfony4_php_1 bash
$ cd /var/www
$ composer create-project symfony/skeleton my_project
```

To set database connection, edit `/var/www/my_project/.env` file, and update `DATABASE_URL` as below:
DATABASE_URL=mysql://root:password@192.168.32.2:3306/my_project_db_name

> IP address above is of `dockerizedsymfony4_mysql_1` container. `dockerizedsymfony4_mysql_1` container's ip address can be checked from it's `/etc/hosts` file, it's appended at the end of it.

> Depending upon your project name above, you might need to update nginx server's root in `/etc/nginx/conf.d/default.conf` file, and point it to your project's public directory. 
> It's currently pointed to `/var/www/my_project/public`

