# Day 3 - Create Subnet

## Context

The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the AWS cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition.

For this task, create one subnet named xfusion-subnet under default VPC.

## Solution

```bash
$ aws ec2 describe-vpcs --filters "Name=isDefault,Values=true" --query "Vpcs[0].VpcId" --output text

$ aws ec2 create-subnet --vpc-id <DEFAULT_VPC_ID> --cidr-block 172.31.96.0/24

$ aws ec2 create-tags --resources <NEW_SUBNET_ID> --tags Key=Name,Value=xfusion-subnet
```

