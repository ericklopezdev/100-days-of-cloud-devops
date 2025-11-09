# Day 1 - Linux User Setup with Non-Interactive Shell

## Context

To accommodate the backup agent tool's specifications, the system admin team at xFusionCorp Industries requires the creation of a user with a non-interactive shell. Here's your task:

Create a user named james with a non-interactive shell on App Server 1.

## Solution

```bash
$ thor@jumphost ~$ ssh tony@stapp01

# The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
# ED25519 key fingerprint is SHA256:ZM6ixMNJCLKDxQXxEVbsd+nllxemuwLp7cIADw.
# This key is not known by any other names
# Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
# Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
# tony@stapp01's password: 

$ [tony@stapp01 ~]$ sudo useradd -s /sbin/nologin james
```
