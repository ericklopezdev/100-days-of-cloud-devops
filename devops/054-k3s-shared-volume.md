# Day 54 - K3s Shared Volume

# Context

We are working on an application that will be deployed on multiple containers within a pod on Kubernetes cluster. There is a requirement to share a volume among the containers to save some temporary data. The Nautilus DevOps team is developing a similar template to replicate the scenario. Below you can find more details about it.

Create a pod named volume-share-nautilus.

For the first container, use image fedora with latest tag only and remember to mention the tag i.e fedora:latest, container should be named as volume-container-nautilus-1, and run a sleep command for it so that it remains in running state. Volume volume-share should be mounted at path /tmp/news.

For the second container, use image fedora with the latest tag only and remember to mention the tag i.e fedora:latest, container should be named as volume-container-nautilus-2, and again run a sleep command for it so that it remains in running state. Volume volume-share should be mounted at path /tmp/demo.

Volume name should be volume-share of type emptyDir.

After creating the pod, exec into the first container i.e volume-container-nautilus-1, and just for testing create a file news.txt with any content under the mounted path of first container i.e /tmp/news.

The file news.txt should be present under the mounted path /tmp/demo on the second container volume-container-nautilus-2 as well, since they are using a shared volume.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

# Solution

```bash
apiVersion: v1
kind: Pod
metadata:
  name: volume-share-nautilus
  labels:
    app: fedora_app
    type: fedora
spec:
  containers:
    - name: volume-container-nautilus-1
      image: fedora:latest
      command: ["/bin/sh", "-c", "while true; do sleep 10; done"]
      volumeMounts:
        - name: volume-share
          mountPath: /tmp/news
      resources:
        requests:
          cpu: 100m
          memory: 100Mi
        limits:
          cpu: 500m
          memory: 500Mi
    - name: volume-container-nautilus-2
      image: fedora:latest
      command: ["/bin/sh", "-c", "while true; do sleep 10; done"]
      volumeMounts:
        - name: volume-share
          mountPath: /tmp/demo
      resources:
        requests:
          cpu: 100m
          memory: 100Mi
        limits:
          cpu: 100m
          memory: 500Mi
  volumes:
    - name: volume-share
      emptyDir: {}
```
```bash
kubectl apply -f k3s-pod.yml
kubectl exec -it volume-share-nautilus -c volume-container-nautilus-1 /bin/sh
touch /tmp/news/news.txt

kubectl exec -it volume-share-nautilus -c volume-container-nautilus-2 /bin/sh
ls /tmp/demo
```
