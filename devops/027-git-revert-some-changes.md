# Day 27 - Git Revert Some Changes

## Context
The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/demo present on Storage server in Stratos DC. However, they reported an issue with the recent commits being pushed to this repo. They have asked the DevOps team to revert repo HEAD to last commit. Below are more details about the task:

In /usr/src/kodekloudrepos/demo git repository, revert the latest commit ( HEAD ) to the previous commit (JFYI the previous commit hash should be with initial commit message ).
Use revert demo message (please use all small letters for commit message) for the new revert commit.

## Solution
```bash
sudo su
cd /usr/src/kodekloudrepos/demo
git log --oneline
git revert HEAD -m "revert demo"
git push
```

### Commit Messages

- **Descriptive**: Explain what is being reverted and why
- **Reference**: Include original commit hash or message
- **Convention**: Follow team's commit message standards
- **Traceability**: Help future developers understand changes

### Safety Considerations

- **Shared Repositories**: Always use revert, never reset
- **Testing**: Test reverted code before pushing
- **Communication**: Inform team about reverted changes
- **Documentation**: Update relevant documentation
