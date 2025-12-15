# Day 37 - Copy File To Docker Container

## Context
The Nautilus DevOps team is conducting application deployment tests on selected application servers. They require completing a task on app server 1.

On Application Server 1 a container named ubuntu_latest is running, you have to copy the encrypted file /tmp/nautilus.tx.gpg from docker hosts to container folder /usr/src.

## Solution
```bash
docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/usr/src/
```
