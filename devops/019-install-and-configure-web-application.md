# Day 19 - Install And Configure Web Application

## Context
xFusionCorp Industries is planning to host two static websites on their infra in Stratos Datacenter. The development of these websites is still in-progress, but we want to get the servers ready. Please perform the following steps to accomplish the task:

Install httpd package and dependencies on app server 3.
Apache should serve on port 6400.
There are two website's backups /home/thor/official and /home/thor/games on jump_host. Set them up on Apache in a way that official should work on the link http://localhost:6400/official/ and games should work on link http://localhost:6400/games/ on the mentioned app server.
Once configured you should be able to access the website using curl command on the respective app server, i.e curl http://localhost:6400/official/ and curl http://localhost:6400/games/

## Solution
```bash
sudo yum install -y httpd
sudo sed -i 's/80/6400/g' /etc/httpd/conf/httpd.conf
sudo systemctl restart httpd
scp -r /home/thor/official banner@stapp03:/home/banner
scp -r /home/thor/games banner@stapp03:/home/banner/
sudo cp -r /home/banner/official /var/www/html/
sudo cp -r /home/banner/games /var/www/html
sudo systemctl restart httpd
curl http://localhost:6400/official/
curl http://localhost:6400/games/
```
