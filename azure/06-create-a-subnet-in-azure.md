# Day 6 - Create a Subnet in Azure

# Context


# Solution
```bash
$ az group list --output table

$ az network vnet create \
    --name datacenter-vnet \
    --resource-group <group-name> \
    --location eastus \
    --address-prefixes 10.0.0.0/16 \
    --subnet-name datacenter-subnet \
    --subnet-prefixes 10.0.0.0/24
```
```
```
```
```
