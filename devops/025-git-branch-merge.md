# Day 25 - Git Branch Merge

## Context
The Nautilus application development team has been working on a project repository /opt/demo.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. They recently shared the following requirements with DevOps team:

Create a new branch nautilus in /usr/src/kodekloudrepos/demo repo from master and copy the /tmp/index.html file (present on storage server itself) into the repo. Further, add/commit this file in the new branch and merge back that branch into master branch. Finally, push the changes to the origin for both of the branches.


## Solution
```bash
sudo su
cd /usr/src/kodekloudrepos/demo
git checkout -b nautilus
cp /tmp/index.html .
git add .
git commit -m "added tmp file"
git switch master
git merge nautilus
git push
```

### Best Practices

- **Clean Branches**: Ensure branches are up-to-date
- **Test Before Merge**: Verify changes work correctly
- **Meaningful Messages**: Write descriptive merge commit messages
- **Delete Merged Branches**: Clean up after successful merge
