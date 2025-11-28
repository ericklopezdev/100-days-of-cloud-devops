# Day 20 - Configure Nginx Plus Php Fpm Using Unix Sock

## Context
The Nautilus application development team is planning to launch a new PHP-based application, which they want to deploy on Nautilus infra in Stratos DC. The development team had a meeting with the production support team and they have shared some requirements regarding the infrastructure. Below are the requirements they shared:

Install nginx on app server 1 , configure it to use port 8093 and its document root should be /var/www/html.
Install php-fpm version 8.2 on app server 1, it must use the unix socket /var/run/php-fpm/default.sock (create the parent directories if don't exist).
Configure php-fpm and nginx to work together.
Once configured correctly, you can test the website using curl http://stapp01:8093/index.php command from jump host.

## Solution
```bash
sudo dnf update -y
sudo dnf install nginx -y
sudo dnf module install php:8.2 -y
sudo mkdir -p /var/run/php-fpm
sudo vi /etc/php-fpm.d/www.conf  # Change listen to /var/run/php-fpm/default.sock
sudo vi /etc/nginx/nginx.conf  # Change port to 8093
sudo vi /etc/nginx/default.d/php.conf  # Change fastcgi_pass to unix:/var/run/php-fpm/default.sock
sudo systemctl enable --now nginx
sudo systemctl enable --now php-fpm
curl http://stapp01:8093/index.php
```
