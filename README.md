# Larapack
Quick start create package laravel

## Installation
```bash
# clone git repository
$ git clone https://github.com/darkjinnee/larapack.git

# go project directory
$ cd ./larapack

# copy .env
$ cp .env.example .env

# up containers
$ docker-compose up --build
```

### Add lines `hosts` file
```text
...
127.0.0.1 larapack.loc www.larapack.loc
```

## Usage
```bash
# commands: start, restart, stop
$ docker-compose <command>

# enter container shell
$ docker-compose exec <service> bash

# show logs containers
$ docker-compose logs -f

# Stop and remove containers, networks, images, and volumes
$ docker-compose down --rmi=all
```

### Migrate and Seeding
```bash
# enter container shell
$ docker-compose exec php bash

# migrate fresh
$ php artisan migrate:fresh --seed
```

### Dev user for PHP service
```bash
$ su dev
```

### Package management
To create packages see the documentation for [laravel-packager](https://github.com/Jeroen-G/laravel-packager)

### Xdebug
To activate Xdebug edit file docker/services/php/conf.d/xdebug.ini, remote host must be your local IP address
***
Multiple domains with [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy "nginx-proxy")
