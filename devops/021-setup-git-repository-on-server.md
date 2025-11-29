# Day 21 - Setup Git Repository On Server

## Context
The Nautilus development team has provided requirements to the DevOps team for a new application development project, specifically requesting the establishment of a Git repository. Follow the instructions below to create the Git repository on the Storage server in the Stratos DC:

Utilize yum to install the git package on the Storage Server.
Create a bare repository named /opt/demo.git (ensure exact name usage).

## Solution
```bash
sudo yum update -y
sudo yum install -y git
sudo git init --bare /opt/demo.git
```

### Repository Naming

- **Convention**: Use `.git` suffix for bare repositories
- **Descriptive Names**: Choose meaningful repository names
- **Path Structure**: Organize repos in logical directory structure
