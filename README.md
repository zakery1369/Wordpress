# Wordpress

![Moodle Docker](https://.png)

- ## How to use this image:

1. Clone or download all files from  [GitHub Page](https://github.com/zakery1369/wordpress/)
2. Download Wordpress from [Wordpress Downloads](https://wordpress.org/download/)
3. Extract Wordpress.zip to the following directory:
```
/var/www/html/wp
```
4. Run the command below :
```
docker-compose up -d
```
5. Open up your web browser, and proceed to the following address to start the installation ( Remember that my configuration will start the server at port 80, in case you want to change the hostname/port, proceed to the next section to customize this image )

```
127.0.0.1
```
6. In the Database settings, adjust the following :
```
Database Name = wordpress
Username = wp
Password = 147258369
Database Host = mysql
Table Prefix = wp_
```


# Customize this image

- ## Use domain with SSL and change Nginx configurations
in the files downloaded from this [GitHub Page](https://github.com/zakery1369/wordpress)
1. In this directory, uncomment the lines in the ``wp.conf`` and replace your domain with **example.com**
```
/nginx/conf.d/wp.conf
```
2. Following the guides from [Letsencrypt](https://letsencrypt.org/getting-started/) (certbot), copy the privkey.pem and fullchain.pem to the following directory. (Remember that from the previous step, the cert files names should correspond with these config file) :
```
/nginx/conf.d/certs
```
3. In case you want to configure your Nginx, you can find the config file in the following directory :
```
/nginx/nginx.conf
```

- ## Change mysql configurations
1. Customize your configs in the following file :
```
/mysql/my.cnf
```
2. Change the mysql environment variables in the docker-compose.yml file :
```
environment:
        MYSQL_ROOT_PASSWORD: 147258369
        MYSQL_DATABASE: wordpress
        MYSQL_USER: wp
        MYSQL_PASSWORD: 147258369
```
- ## Change php-fpm configurations
Add your customized configurations in these files :
```
/php-fpm/php.ini-development
/php-fpm/php.ini-production
/php-fpm/www.conf
/php-fpm/php.ini
```

- ## Exposing external port
Edit docker-compose.yml to change the exposed ports :
``` 
ports:
     - 80:80
     - 443:443
```

