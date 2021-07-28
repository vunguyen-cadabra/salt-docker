Docker setup
===============

The Docker environment project.

## Directory structure
```
├─ docker-compose.yml
│
├─ apache
│   └─ vhost.conf
│
├─ centos-apache-php
│   └─ Dockerfile
│
├─ .env.example
│
├─ .gitignore
│
```

## Setup manual
**1. Install Docker Desktop on Windows**:

- Download Docker Desktop for Windows. </br>
  https://hub.docker.com/editions/community/docker-ce-desktop-windows/

(*) Requires Microsoft Windows 10 Professional or Enterprise 64-bit, or Windows 10 Home 64-bit with WSL 2.

**2. Modify project path**

Copy and rename the '.env.example' file to '.env'.

Modify the source directory in .env file.
```
SOURCE_PATH=<SOURCE DIRECTORY>
```

- Application will be mounted to `/opt/www/salt-old/race_custom/salt_crm`
 
You may modify project paths <SOURCE DIRECTORY> in above directory with your local paths.

Eg:
```
SOURCE_PATH=../laravel-vue-project
```

- Modify others configurations if needed.</br>
eg: you can modify the port number of http/https instead of the default configuration shown below.
```
APP_PORT=80
APP_SSL_PORT=443
```

**4. Build docker**

By using window command line ..etc<br />

1/ Go to docker's directory.<br />
2/ Build image by command.<br />
```bash
docker-compose build
```

3/ Build containner.																				
```bash
docker-compose up
```

4/ Build image and Build containner.																				
```bash
docker-compose up -d
```

if it's all successed, all the services are running as image below
![Mount](wiki/docker-desktop.JPG)

**5. Access local site**

http://localhost/

* if the default port 80/443 has modified in .env file, it's must be specified in the url properly.

## Useful commands inside container

Get inside a containner
eg:
```bash
    docker exec -it docker_phpfpm_1 bash
```

Show docker images (run on host machine)
```bash
docker ps
```									

- (Optional) Show all images (run on host machine):
```bash
docker images
```

## Modify the DB mysql connection of laravel-vue-project
1. In .env file, modify the config:
```bash
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=CMSF
DB_USERNAME=salt_user
DB_PASSWORD=123456
```
