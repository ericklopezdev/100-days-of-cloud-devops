# Day 41 - Create A Docker File

## Context
Create a Docker File
As per recent requirements shared by the Nautilus application development team, they need custom images created for one of their projects. Several of the initial testing requirements are already been shared with DevOps team. Therefore, create a docker file /opt/docker/Dockerfile (please keep D capital of Dockerfile) on App server 2 in Stratos DC and configure to build an image with the following requirements:

Use ubuntu:24.04 as the base image.

Install apache2 and configure it to work on 5002 port. (do not update any other Apache configuration settings like document root etc).

## Solution
```dockerfile
FROM ubuntu:24.04
RUN apt update && apt install -y apache2
RUN sed -i 's/80/5002/g' /etc/apache2/ports.conf /etc/apache2/sites-enabled/000-default.conf
EXPOSE 5002
CMD ["apache2ctl", "-D", "FOREGROUND"]
```
