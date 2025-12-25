# Day 47 - Docker Python App

## Context
A python app needed to be Dockerized, and then it needs to be deployed on App Server 3. We have already copied a requirements.txt file (having the app dependencies) under /python_app/src/ directory on App Server 3. Further complete this task as per details mentioned below:

Create a Dockerfile under /python_app directory:

Use any python image as the base image.
Install the dependencies using requirements.txt file.
Expose the port 6300.
Run the server.py script using CMD.
Build an image named nautilus/python-app using this Dockerfile.

Once image is built, create a container named pythonapp_nautilus:

Map port 6300 of the container to the host port 8096.
Once deployed, you can test the app using curl command on App Server 3.

## Solution
```dockerfile
FROM python:3.9.23-slim
WORKDIR /app
COPY ./src/* /app/
RUN pip install -r requirements.txt
EXPOSE 6300
CMD ["python", "server.py"]
```

```bash
docker build -t nautilus/python-app .
docker run -d --name pythonapp_nautilus -p 8096:6300 nautilus/python-app
curl http://localhost:8096
```
