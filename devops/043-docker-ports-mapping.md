# Day 43 - Docker Ports Mapping

## Context
The Nautilus DevOps team is planning to host an application on a nginx-based container. There are number of tickets already been created for similar tasks. One of the tickets has been assigned to set up a nginx container on Application Server 2 in Stratos Datacenter. Please perform the task as per details mentioned below:

Pull nginx:stable docker image on Application Server 2.

Create a container named cluster using the image you pulled.

Map host port 5002 to container port 80. Please keep the container in running state.

## Solution
```bash
docker pull nginx:stable
docker run -d --name cluster -p 5002:80 nginx:stable
```
