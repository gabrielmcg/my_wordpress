# my_wordpress

```

git clone https://github.com/gabrielmcg/my_wordpress.git

cd my_wordpress

docker-compose up -d


http://ip172-18-0-7-*************-8000.direct.labs.play-with-docker.com/wp-admin/install.php

docker ps -qf "name=mywordpress_wordpress_1"

docker exec -it mywordpress_wordpress_1 /bin/bash
```

Search for JWT plug-in
http://ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com/wp-admin/plugin-install.php?s=jwt&tab=search&type=term

Install JWT Authentication for WP REST API
http://ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com/wp-admin/plugin-install.php?tab=plugin-information&plugin=jwt-authentication-for-wp-rest-api&TB_iframe=true&width=600&height=550

Activate
http://ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com/wp-admin/plugins.php?_wpnonce=be9e0fbde6&action=activate&plugin=jwt-authentication-for-wp-rest-api/jwt-auth.php

View Details
http://ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com/wp-admin/plugin-install.php?tab=plugin-information&plugin=jwt-authentication-for-wp-rest-api&TB_iframe=true&width=772&height=712



```
apt-get update
apt-get install vim
```




```
$ docker exec -it mywordpress_wordpress_1 /bin/bash
root@fc2cdbcc8d6a:/var/www/html# ls
index.php    wp-activate.php     wp-comments-post.php  wp-content   wp-links-opml.php  wp-mail.php      wp-trackback.php
license.txt  wp-admin            wp-config-sample.php  wp-cron.php  wp-load.php        wp-settings.php  xmlrpc.php
readme.html  wp-blog-header.php  wp-config.php         wp-includes  wp-login.php       wp-signup.php


root@fc2cdbcc8d6a:/var/www/html# ls -al
total 196
drwxr-xr-x  5 www-data www-data  4096 Feb  1 22:19 .
drwxr-xr-x  1 root     root        18 Jan  4 01:30 ..
-rw-r--r--  1 www-data www-data   235 Feb  1 22:20 .htaccess
-rw-r--r--  1 www-data www-data   418 Sep 25  2013 index.php
-rw-r--r--  1 www-data www-data 19935 Jan  6 19:32 license.txt
-rw-r--r--  1 www-data www-data  7413 Dec 12  2016 readme.html
-rw-r--r--  1 www-data www-data  5434 Sep 23 12:21 wp-activate.php
drwxr-xr-x  9 www-data www-data  4096 Jan 16 21:39 wp-admin
-rw-r--r--  1 www-data www-data   364 Dec 19  2015 wp-blog-header.php
-rw-r--r--  1 www-data www-data  1627 Aug 29  2016 wp-comments-post.php
-rw-r--r--  1 www-data www-data  2764 Feb  1 22:19 wp-config-sample.php
-rw-r--r--  1 www-data www-data  3154 Feb  1 22:19 wp-config.php
drwxr-xr-x  5 www-data www-data    67 Feb  1 22:31 wp-content
-rw-r--r--  1 www-data www-data  3669 Aug 20 04:37 wp-cron.php
drwxr-xr-x 18 www-data www-data  8192 Jan 16 21:39 wp-includes
-rw-r--r--  1 www-data www-data  2422 Nov 21  2016 wp-links-opml.php
-rw-r--r--  1 www-data www-data  3306 Aug 22 11:52 wp-load.php
-rw-r--r--  1 www-data www-data 36583 Oct 13 02:10 wp-login.php
-rw-r--r--  1 www-data www-data  8048 Jan 11  2017 wp-mail.php
-rw-r--r--  1 www-data www-data 16246 Oct  4 00:20 wp-settings.php
-rw-r--r--  1 www-data www-data 30071 Oct 18 17:36 wp-signup.php
-rw-r--r--  1 www-data www-data  4620 Oct 23 22:12 wp-trackback.php
-rw-r--r--  1 www-data www-data  3065 Aug 31  2016 xmlrpc.php
root@fc2cdbcc8d6a:/var/www/html#


```

To enable this option you’ll need to edit your .htaccess file adding the follow

vi .htaccess

```
RewriteEngine on


RewriteCond %{HTTP:Authorization} ^(.*)
RewriteRule ^(.*) - [E=HTTP_AUTHORIZATION:%1]

SetEnvIf Authorization "(.*)" HTTP_AUTHORIZATION=$1
```

vi wp-config.php

```
define('JWT_AUTH_SECRET_KEY', 'your-top-secrect-key');
define('JWT_AUTH_CORS_ENABLE', true);
```

exit



```
docker volume ls
DRIVER              VOLUME NAME
local               fe191a97abe319fba338b2b8898b219d41973a1f0d0080c1570e326ecf4663bb
local               mywordpress_db_data
[node1] (local) root@192.168.0.158 ~/my_wordpress



[node1] (local) root@192.168.0.158 ~/my_wordpress
$ docker volume inspect fe191a97abe319fba338b2b8898b219d41973a1f0d0080c1570e326ecf4663bb
[
    {
        "CreatedAt": "2018-02-01T23:08:02Z",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/fe191a97abe319fba338b2b8898b219d41973a1f0d0080c1570e326ecf4663bb/_data",
        "Name": "fe191a97abe319fba338b2b8898b219d41973a1f0d0080c1570e326ecf4663bb",
        "Options": {},
        "Scope": "local"
    }
]
[node1] (local) root@192.168.0.158 ~/my_wordpress
```

```
node1] (local) root@192.168.0.158 ~/my_wordpress
$ docker-compose stop
Stopping mywordpress_wordpress_1 ... done
Stopping mywordpress_db_1        ... done
[node1] (local) root@192.168.0.158 ~/my_wordpress
$ docker-compose up -d
Starting mywordpress_db_1 ... done
Starting mywordpress_wordpress_1 ... done
[node1] (local) root@192.168.0.158 ~/my_wordpress
$ docker exec -it mywordpress_wordpress_1 /bin/bash
root@fc2cdbcc8d6a:/var/www/html# ls
index.php    wp-activate.php     wp-comments-post.php  wp-content   wp-links-opml.php  wp-mail.php      wp-trackback.php
license.txt  wp-admin            wp-config-sample.php  wp-cron.php  wp-load.php        wp-settings.php  xmlrpc.php
readme.html  wp-blog-header.php  wp-config.php         wp-includes  wp-login.php       wp-signup.php
root@fc2cdbcc8d6a:/var/www/html# more .htaccess
# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]

RewriteCond %{HTTP:Authorization} ^(.*)
RewriteRule ^(.*) - [E=HTTP_AUTHORIZATION:%1]

SetEnvIf Authorization "(.*)" HTTP_AUTHORIZATION=$1

</IfModule>

# END WordPress
```


The files are stored in a VOLUME inn Dockerfile, so survive restart:

VOLUME /var/www/html



http://ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com/wp-json

{"name":"My WordPress","description":"Just another WordPress site","url":"http:\/\/ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com","home":"http:\/\/ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com","gmt_offset":"0","timezone_string":"","namespaces":["oembed\/1.0","jwt-auth\/v1","wp\/v2"],"authentication":[],"routes":{"\/":{"namespace":"","methods":["GET"],"endpoints":[{"methods":["GET"],"args":{"context":{"required":false,"default":"view"}}}],"_links":{"self":"http:\/\/ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com\/wp-json\/"}},"\/oembed\/1.0":{"namespace":"oembed\/1.0","methods":["GET"],



http://ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com/wp-json/wp/v2/posts

[{"id":1,"date":"2018-02-01T22:20:10","date_gmt":"2018-02-01T22:20:10","guid":{"rendered":"http:\/\/ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com\/?p=1"},"modified":"2018-02-01T22:20:10","modified_gmt":"2018-02-01T22:20:10","slug":"hello-world","status":"publish","type":"post","link":"http:\/\/ip172-18-0-25-b9pp4c2r91k000b18afg-8000.direct.labs.play-with-docker.com\/2018\/02\/01\/hello-world\/","title":{"rendered":"Hello world!"},"content":{"rendered":"<p>Welcome to WordPress. This is your first post. Edit or delete it, then start writing!<\/p>\n","protected":false},"excerpt":{"rendered":"<p>Welcome to WordPress. This is your first post. Edit or delete it, then start writing!
    
    
    
    
    













