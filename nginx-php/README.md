NGINX & PHP
=============

PHP 7 and Nginx

```
docker run -d -p 8100:80 -v /home/containers/web:/var/www/html muteor/nginx-php
docker run -d -p 8100:80 -v /home/containers/web:/var/www/html -e VIRTUAL_HOST=php.web.foo.io muteor/nginx-php
```
