# Day 1 - Create Key Pair

## Context

The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the AWS cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition. To achieve this, they have segmented large tasks into smaller, more manageable units. This granular approach enables the team to execute the migration in gradual phases, ensuring smoother implementation and minimizing disruption to ongoing operations. By breaking down the migration into smaller tasks, the Nautilus DevOps team can systematically progress through each stage, allowing for better control, risk mitigation, and optimization of resources throughout the migration process.

## Solution

```bash
$ aws --version
aws-cli/1.40.19 Python/3.10.17 Linux/5.15.0-1083-gcp botocore/1.38.20

$ aws ec2 create-key-pair \
    --key-name xfusion-kp \
    --key-type rsa \
    --region us-east-1 \
    --query 'KeyMaterial' \
    --output text > xfusion-kp.pem

$ ls
xfusion-kp.pem

$ chmod 400 xfusion-kp.pem

$ aws ec2 describe-key-pairs --key-names xfusion-kp --region us-east-1
```

