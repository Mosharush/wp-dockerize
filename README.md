# WP Dockerize
## Wordpress Docker Development Project

Wordpress clean project with docker services for mysql8, phpmyadmin & wordpress server.

### How to use
#### Run services:
```
docker-compose -f docker-compose.yml -f docker-compose.http.yml up -d
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
docker-compose down --remove && docker-compose -f docker-compose.yml -f docker-compose.http.yml up --force-recreate --build -d
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

## SSL Support
If you need a https connection on your local machine you can run nginx server with self-signed certificate pass over proxy to wordpress server.
We take care about it, you just need to do follow:

I was setup simple conf for SSL Certificate with mock data on `nginx/server.csr.cnf`. If you want to setup the real data you can edit the file *before* run the generate script.

To support multiple domains on certificate you can edit `v3.ext` file and add more domains, eg:
```
....
[alt_names]
DNS.1 = localhost
DNS.2 = www.domain.com
DNS.3 = domain.com
DNS.4 = www.domain.dev
DNS.5 = domain.dev
```

After you finish optionally pre-setup steps, Go to terminal, navigate to nginx dir then add execution permissions to `./generateKeyAndCert.sh` script.
```
cd nginx/
chmod +x ./generateKeyAndCert.sh 
```

Now we can run auto setup to generate ssl keys:
```
./generateKeyAndCert.sh
```

You will asked for add the certificate to trusted root of your computer, answer y to accept or n to ignore.
This will solve browsers issues with self-sign certificates and will show you green lock on browser's url bar.

#### Run services with SSL (over nginx server):
```
docker-compose -f docker-compose.yml -f docker-compose.https.yml up -d
```
OR
```
npm run ssl
```

* Feature: when we using nginx server I added alias for phpmyadmin, so from now you can just go to https://localhost/phpmyadmin

## Up to next...
- Auto Import DB on start.
- And more...