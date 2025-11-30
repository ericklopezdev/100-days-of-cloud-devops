# Day 22 - Clone Git Repository

## Context
The DevOps team established a new Git repository last week, which remains unused at present. However, the Nautilus application development team now requires a copy of this repository on the Storage Server in the Stratos DC. Follow the provided details to clone the repository

The repository to be cloned is located at /opt/games.git
Clone this Git repository to the /usr/src/kodekloudrepos directory. Ensure no modifications are made to the repository during the cloning process.

## Solution
```bash
cd /usr/src/kodekloudrepos
git clone /opt/games.git
```

### Post-Clone Setup

- **Remote Origin**: Automatically configured
- **Default Branch**: Checked out automatically
- **Tracking Branches**: Set up for push/pull operations
- **Configuration**: Inherits repository settings
