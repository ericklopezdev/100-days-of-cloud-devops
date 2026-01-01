# Day 1 - Create SSH Key Pair for Azure Virtual Machine

## Context 

The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the Azure cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition. To achieve this, they have segmented large tasks into smaller, more manageable units. This granular approach enables the team to execute the migration in gradual phases, ensuring smoother implementation and minimizing disruption to ongoing operations. By breaking down the migration into smaller tasks, the Nautilus DevOps team can systematically progress through each stage, allowing for better control, risk mitigation, and optimization of resources throughout the migration process.

## Solution 

```bash
$ showcreds

# used the web platform, with user account and the temp password for access
$ az login

$ az group list --output table

$ az sshkey create --name "nautilus-kp" --resource-group "GROUP" --location "eastus"
```
