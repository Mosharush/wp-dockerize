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
#### Stop services:
```
docker-compose down
```
OR
```
npm stop
```

---
#### Rebuild docker images & containers:
```
docker-compose down --remove && docker-compose up --force-recreate --build -d
```

### Application
#### WordPress
After all services running we can visit our WordPress website on one of this urls:

http://127.0.0.1

http://localhost

We can change the web server port on `docker-compose.yml` file.

---
#### PhpMyAdmin
For a custom manage of our database we have PMA Application on one of this urls: 

http://127.0.0.1:8080

http://localhost:8080

---
#### MySQL
The MySQL Server is running in background and for see the data in visual we can use the PhpMyAdmin Application.

But if for some reasons we want to connect to him is will be available with this data connection:

-- *Database Host:* `localhost`

-- *Database Port:* `3306`

-- *Database User Name:* `root`

-- *Database User Password:* `MyStr0ngP455`

-- *WordPress Database Name:* `wordpress`
