# Day 28 - Git Cherry Pick

## Context
The Nautilus application development team has been working on a project repository /opt/official.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. They recently shared the following requirements with the DevOps team:

There are two branches in this repository, master and feature. One of the developers is working on the feature branch and their work is still in progress, however they want to merge one of the commits from the feature branch to the master branch, the message for the commit that needs to be merged into master is Update info.txt. Accomplish this task for them, also remember to push your changes eventually.

## Solution
```bash
sudo su
cd /usr/src/kodekloudrepos/official
git branch
git log --oneline  # In feature branch, find commit hash
git switch master
git cherry-pick commit-hash
git push
```

### Conflict Resolution

- **Automatic**: Git applies changes if no conflicts
- **Manual**: Resolve conflicts like in merge operations
- **Continue**: `git cherry-pick --continue` after resolving
- **Abort**: `git cherry-pick --abort` to cancel operation
