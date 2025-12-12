# Day 34 - Configure Git Hook

## Context
The Nautilus application development team was working on a git repository /opt/demo.git which is cloned under /usr/src/kodekloudrepos directory present on Storage server in Stratos DC. The team want to setup a hook on this repository, please find below more details:

Merge the feature branch into the master branch`, but before pushing your changes complete below point.

Create a post-update hook in this git repository so that whenever any changes are pushed to the master branch, it creates a release tag with name release-2023-06-15, where 2023-06-15 is supposed to be the current date. For example if today is 20th June, 2023 then the release tag must be release-2023-06-20. Make sure you test the hook at least once and create a release tag for today's release.

Finally remember to push your changes.

## Solution
```bash
sudo -i
cd /usr/src/kodekloudrepos/demo
git switch master
git merge feature
cp /opt/demo.git/hooks/post-update.sample /opt/demo.git/hooks/post-update
chmod +x /opt/demo.git/hooks/post-update
vi /opt/demo.git/hooks/post-update  # Add day=$(date +"%Y-%m-%d"); TAG="release-$day"; git tag -a $TAG -m "Released at: $day"
git push
git fetch --tags
git tag
```

### Hook Implementation

- **Location**: `.git/hooks/` directory
- **Executable**: Must have execute permissions
- **Language**: Any scripting language (bash, Python, etc.)
- **Exit Codes**: Non-zero exit prevents operation (pre-hooks)

### Common Use Cases

- **Code Quality**: Run linters, formatters
- **Testing**: Execute test suites before commits
- **Deployment**: Automatic deployment on push
- **Notifications**: Send alerts on repository changes
- **Tagging**: Automatic version tagging
