# 007-linux-ssh-authentication

## Context

The system admins team of xFusionCorp Industries has set up some scripts on jump host that run on regular intervals and perform operations on all app servers in Stratos Datacenter. To make these scripts work properly we need to make sure the thor user on jump host has password-less SSH access to all app servers through their respective sudo users (i.e tony for app server 1). Based on the requirements, perform the following:

Set up a password-less authentication from user thor on jump host to all app servers through their respective sudo users.


## Solution

```bash
sudo su - thor
ssh-keygen -t rsa
for user_host in "tony@stapp01" "steve@stapp02" "banner@stapp03"; do
    ssh-copy-id $user_host
done
```

