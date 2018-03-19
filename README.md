# nginx-php-fmp-pgsql
Docker PHP 7.2.3 environment
## Structure
```
Project container
|
├── nginx-php-fmp-pgsql
│   ├── nginx
│   ├── ...
│   └── ...
├── dbdata [mounted volume]
└── project
    ├── ...
    ├── public [mounted volume]
    |   ├── served
    |   └── files
    └── ...
```
## Run
```docker-compose up```
## Building blocks properties
#### Nginx server
- version: 1.13.9
- container name: **nginx**
- port mapping:
  - host: ```http://<DOCKER_HOST>:8000```
  - container: ```http://nginx:80```
- mounted volumes:
  - ```../project``` on ```/var/www/html```
  - ```../nginx/site.conf``` on ```/etc/nginx/conf.d/default.conf```
- depends on: **php-fpm**

#### PHP-FPM
- php version: 7.2.3
- container name: **php-fpm**
- working directory: ```/var/www/html```
- mounted volume: ```../project``` on ```/var/www/html```

#### Adminer (database manager)
- version: 4.6.2
- container name: **adminer**
- port mapping:
  - host: ```http://<DOCKER_HOST>:8080```
  - container: ```http://adminer:8080```

#### Postgresql
- version: 9.6.7
- container name: **pgsql**
- port mapping:
  - host: ```http://<DOCKER_HOST>:5432```
  - container: ```http://pgsql:5432```
- mounted volume: ```../dbdata``` on ```/var/lib/postgresql/data```
- DB user: *user*
- DB password: *password*
- DB name: *dbname*