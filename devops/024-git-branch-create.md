# Day 24 - Git Branch Create

## Context
Nautilus developers are actively working on one of the project repositories, /usr/src/kodekloudrepos/media. Recently, they decided to implement some new features in the application, and they want to maintain those new changes in a separate branch. Below are the requirements that have been shared with the DevOps team:

On Storage server in Stratos DC create a new branch xfusioncorp_media from master branch in /usr/src/kodekloudrepos/media git repo.

Please do not try to make any changes in the code.

## Solution
```bash
sudo su
cd /usr/src/kodekloudrepos/media
git switch master
git checkout -b xfusioncorp_media
```

### Branching Strategies

- **Feature Branches**: Separate branch for each feature
- **Git Flow**: master, develop, feature, release, hotfix branches
- **GitHub Flow**: Simple master + feature branch workflow
- **Release Branches**: Prepare releases without blocking development

### Best Practices

- **Descriptive Names**: Use clear, meaningful branch names
- **Short-lived**: Keep feature branches small and focused
- **Regular Updates**: Sync with main branch frequently
- **Clean History**: Use meaningful commit messages
