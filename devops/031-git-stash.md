# Day 31 - Git Stash

## Context
The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/ecommerce present on Storage server in Stratos DC. One of the developers stashed some in-progress changes in this repository, but now they want to restore some of the stashed changes. Find below more details to accomplish this task:

Look for the stashed changes under /usr/src/kodekloudrepos/ecommerce git repository, and restore the stash with stash@{1} identifier. Further, commit and push your changes to the origin.

## Solution
```bash
sudo -i
cd /usr/src/kodekloudrepos/ecommerce
git stash list
git stash apply stash@{1}
git add .
git commit -m "Restored stash files"
git push
```

### Advanced Stashing

- **Include Untracked**: `git stash -u` includes new files
- **Include Ignored**: `git stash -a` includes ignored files
- **Branch from Stash**: `git stash branch name` creates branch
- **Show Changes**: `git stash show -p stash@{n}` displays diff
