# Day 18 - Configure Lamp Server Lamp Stack

## Context
xFusionCorp Industries is planning to host a WordPress website on their infra in Stratos Datacenter. They have already done infrastructure configuration—for example, on the storage server they already have a shared directory /vaw/www/html that is mounted on each app host under /var/www/html directory. Please perform the following steps to accomplish the task:

Install httpd,php and its dependencies on all app hosts.
Apache should serve on port 3003 within the apps.
Install/Configure MariaDB server on DB Server.
Create a database named kodekloud_db2 and create a database user named kodekloud_cap identified as password your-pass. Further make sure this newly created user is able to perform all operation on the database you created.
Finally you should be able to access the website on LBR link, by clicking on the App button on the top bar. You should see a message like App is able to connect to the database using user kodekloud_cap

## Solution
```bash
# On app servers
sudo yum install -y httpd php php-mysqli
sudo sed -i 's/80/3003/g' /etc/httpd/conf/httpd.conf
sudo systemctl enable --now httpd

# On DB server
sudo yum install -y mariadb-server
sudo systemctl enable --now mariadb
mysql -u root -e "CREATE DATABASE kodekloud_db2;"
mysql -u root -e "CREATE USER 'kodekloud_cap'@'%' IDENTIFIED BY 'your-pass';"
mysql -u root -e "GRANT ALL ON kodekloud_db2.* TO 'kodekloud_cap'@'%';"
mysql -u root -e "FLUSH PRIVILEGES;"
```
