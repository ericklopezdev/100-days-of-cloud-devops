# Day 35 - Setup Docker Installation

## Context
The Nautilus DevOps team aims to containerize various applications following a recent meeting with the application development team. They intend to conduct testing with the following steps:

Install docker-ce and docker compose packages on App Server 2.
Initiate the docker service.

## Solution
```bash
sudo yum update -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo systemctl enable docker.service
sudo systemctl start docker.service
```
