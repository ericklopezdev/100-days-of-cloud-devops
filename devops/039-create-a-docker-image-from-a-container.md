# Day 39 - Create A Docker Image From A Container

## Context
One of the Nautilus developer was working to test new changes on a container. He wants to keep a backup of his changes to the container. A new request has been raised for the DevOps team to create a new image from this container. Below are more details about it:

- Create an image `ecommerce:nautilus` on `Application Server 3` from a container `ubuntu_latest` that is running on same server.

# Solution


```bash
docker commit ubuntu_latest ecommerce:nautilus
```
