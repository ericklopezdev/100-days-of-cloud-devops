# Day 53 - Resolve Volumemounts Issue In Kubernetes

## Context
We encountered an issue with our Nginx and PHP-FPM setup on the Kubernetes cluster this morning, which halted its functionality. Investigate and rectify the issue:

The pod name is nginx-phpfpm and configmap name is nginx-config. Identify and fix the problem.

Once resolved, copy /home/thor/index.php file from the jump host to the nginx-container within the nginx document root. After this, you should be able to access the website using Website button on the top bar.

Note: The kubectl utility on jump_host is configured to operate with the Kubernetes cluster.

## Solution
```bash
kubectl get pod nginx-phpfpm -o yaml > nginx-phpfpm.yml
# Edit nginx container mountPath to /var/www/html for shared-files
kubectl delete pod nginx-phpfpm
kubectl apply -f nginx-phpfpm.yml
kubectl cp /home/thor/index.php nginx-phpfpm:/var/www/html/index.php -c nginx-container
```