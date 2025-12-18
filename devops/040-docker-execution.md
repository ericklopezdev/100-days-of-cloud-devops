# Day 40 - Docker Execution

## Context
One of the Nautilus DevOps team members was working to configure services on a kkloud container that is running on App Server 1 in Stratos Datacenter. Due to some personal work he is on PTO for the rest of the week, but we need to finish his pending work ASAP. Please complete the remaining work as per details given below:

Install apache2 in kkloud container using apt that is running on App Server 1 in Stratos Datacenter.

Configure Apache to listen on port 6000 instead of default http port. Do not bind it to listen on specific IP or hostname only, i.e it should listen on localhost, 127.0.0.1, container ip, etc.

Make sure Apache service is up and running inside the container. Keep the container in running state at the end.

## Solution
```bash
docker exec -it kkloud /bin/bash
apt install apache2 vim -y
vi /etc/apache2/ports.conf  # Change Listen 80 to 6000
vi /etc/apache2/sites-enabled/000-default.conf  # Change <VirtualHost *:80> to *:6000
/usr/sbin/apache2ctl start
curl localhost:6000
```
