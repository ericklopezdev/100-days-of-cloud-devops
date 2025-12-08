# Day 30 - Git Reset Hard

## Context
The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/ecommerce present on Storage server in Stratos DC. This was just a test repository and one of the developers just pushed a couple of changes for testing, but now they want to clean this repository along with the commit history/work tree, so they want to point back the HEAD and the branch itself to a commit with message add data.txt file. Find below more details:

In /usr/src/kodekloudrepos/ecommerce git repository, reset the git commit history so that there are only two commits in the commit history i.e initial commit and add data.txt file.

Also make sure to push your changes.

## Solution
```bash
sudo -i
cd /usr/src/kodekloudrepos/ecommerce
git log --oneline
git reset --hard commit-hash-of-add-data.txt
git push --force
```

### Recovery Options

- **Reflog**: `git reflog` shows recent HEAD movements
- **Recovery**: `git reset --hard HEAD@{n}` to restore
- **Time Limit**: Reflog entries expire after ~90 days
- **Garbage Collection**: `git gc` can remove unreachable commits
