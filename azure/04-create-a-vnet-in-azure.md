# Day 4 - Create a VNET in Azure

# Context

The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the Azure cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition. To achieve this, they have segmented large tasks into smaller, more manageable units. This granular approach enables the team to execute the migration in gradual phases, ensuring smoother implementation and minimizing disruption to ongoing operations.

Create a Virtual Network (VNet) named xfusion-vnet in the East US region with any IPv4 CIDR block.

# Solution

```bash
az network vnet create \
  --name xfusion-vnet \
  --resource-group nautilus-rg \
  --location eastus \
  --address-prefixes 10.0.0.0/16 \
  --subnet-name default-subnet \
  --subnet-prefixes 10.0.1.0/24
```