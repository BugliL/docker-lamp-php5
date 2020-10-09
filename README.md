![Docker-LAMP](https://cdn.rawgit.com/mattrayner/docker-lamp/831976c022782e592b7e2758464b2a9efe3da042/docs/logo.svg)

Docker-LAMP-PHP5 is a Docker image that includes the Phusion base along with a
LAMP stack ([Apache 2.4.7](http://www.apache.org/), [MySQL
5.7](https://www.mysql.com/) and [PHP 5.6](http://php.net/)) on Ubuntu 16.04
Xenial, all in one handy container. [phpMyAdmin](https://www.phpmyadmin.net/)
is also bundled.

**This image is only intended for legacy PHP 5.6 applications, which is
[end-of-life](https://www.php.net/supported-versions.php) as of January 2019.
Use at your own risk, preferably *not* in production and/or public-facing
environments!**

Based off an old version of
[mattrayner/docker-lamp](https://github.com/mattrayner/docker-lamp).


## Usage

### Directory structure

``` 
/ (project root) 
/app/ (your PHP files aka the web root) 
/mysql/ (Docker will create this and store your MySQL data here) 
```

### Starting from command line

```
docker build -t buglil/lamp .
docker run -p "8080:80" -v /home/buglil/Desktop/plservice1:/app -v ${pwd}/mysql:/var/lib/mysql buglil/lamp:latest 
```

### MySQL Databases

When you first run the image, you'll see a message showing your `admin` user's
password. This is the user you should use in your application. If you need this
login later, you can run `docker logs CONTAINER_ID` and you should see it at
the top of the log.

You can access [phpMyAdmin](https://www.phpmyadmin.net/) at `/phpmyadmin` with
the `admin` username and password.

By default, the image comes with a `root` MySQL account that has no password.
This account is only available locally, i.e. within your application. It is not
available from outside your Docker image or through phpMyAdmin.

## Change mysql root password

```
SET PASSWORD for 'root'@'localhost' = password('enteryourpassword');
```


## License Docker-LAMP is licensed under the [Apache 2.0 License](LICENSE.md).
