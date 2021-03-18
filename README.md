# docker-compose-laravel
A Docker Compose workflow that sets up a LEMP network of containers for local Laravel development.


## Usage

To get started, make sure you have [Docker installed](https://docs.docker.com/get-docker/) on your system, and then clone all files from that repository to your laravel project.

By default php version is 7.4
If you want use other version set `PHP_VERSION=72` variable in `.env`.

If you do not have installed mysql locally please uncomment mysql container parts in `docker-compose.yml` file.

If you want use custom domain for your local app please set `NGINX_SERVER_NAME=customdomain.local` variable in `.env` file (by default it is `localhost`), , add domain to `/etc/hosts` 

Next, run the command from project directory `docker-compose up -d --build app`

Available services:

- **nginx** - `:80`
- **mysql** - `:3306` if use
- **php** - `:9000`
- **redis** - `:6379`
- **mailhog** - `:8025`, `:1025` 

For running common commands use:

- `docker exec -ti php /bin/sh` - open bash for app
- `docker exec -ti php composer` -  composer or use it from php bash 
- `docker exec -ti php php artisan` - artisan or use it from php bash
- `docker-compose run --rm npm run dev`
- `docker-compose run --rm npm run watch`
- `docker-compose run --rm npm run prod` 


## .env configuration

### MYSQL

- `DB_HOST=host.docker.internal` - If you use local MYSQL (MacOs)
- `DB_HOST=172.17.0.1` - If you use local MYSQL (Linux)
- `DB_HOST=mysql` - If you use docker mysql image

### CACHE

- `CACHE_DRIVER=redis`
- `REDIS_HOST=redis`

### MAIL

```
MAIL_DRIVER=smtp
MAIL_HOST=mailhog
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS=from@example.com
MAIL_FROM_NAME=Example
```

To see the dashboard and view any emails coming through the system, visit [localhost:8025](http://localhost:8025) after running `docker-compose up -d app`.


