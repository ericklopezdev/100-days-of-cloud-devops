# Day 05 - Create a VNET IPV4

# Contex

The Nautilus DevOps team is strategically planning the migration of a portion of their infrastructure to the Azure cloud. Acknowledging the magnitude of this endeavor, they have chosen to tackle the migration incrementally rather than as a single, massive transition. Their approach involves creating Virtual Networks (VNets) as the initial step, as they will be provisioning various services under different VNets.

Create a Virtual Network (VNet) named datacenter-vnet in the East US region with 192.168.0.0/24 IPv4 CIDR.

# Solution

```bash
$ az group list --output table

$ az network vnet create \
  --name datacenter-vnet \
  --resource-group nautilus-rg \
  --location eastus \
  --address-prefix 192.168.0.0/24
```
