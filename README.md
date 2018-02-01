# my_wordpress

```

git clone https://github.com/gabrielmcg/my_wordpress.git

cd my_wordpress

docker-compose up -d


http://ip172-18-0-7-*************-8000.direct.labs.play-with-docker.com/wp-admin/install.php

docker ps -qf "name=mywordpress_wordpress_1"

docker exec -it mywordpress_wordpress_1 /bin/bash
``


```
$ docker exec -it mywordpress_wordpress_1 /bin/bash
root@fc2cdbcc8d6a:/var/www/html# ls
index.php    wp-activate.php     wp-comments-post.php  wp-content   wp-links-opml.php  wp-mail.php      wp-trackback.php
license.txt  wp-admin            wp-config-sample.php  wp-cron.php  wp-load.php        wp-settings.php  xmlrpc.php
readme.html  wp-blog-header.php  wp-config.php         wp-includes  wp-login.php       wp-signup.php
```
