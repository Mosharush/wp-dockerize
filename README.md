# WP Dockerize
## Wordpress Docker Development Project

Wordpress clean project with docker services for mysql8, phpmyadmin & wordpress server.

### How to use
#### Run services:
```
docker-compose up -d
```
OR
```
npm start
```
---
#### Run services:
```
docker-compose down
```
OR
```
npm stop
```
---
#### To do full rebuild docker images & containers:
```
docker-compose down --remove && docker-compose up --force-recreate --build -d
```