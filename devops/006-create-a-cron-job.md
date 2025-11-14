# setup_a_cron_job

## Context

The Nautilus system admins team has prepared scripts to automate several day-to-day tasks. They want them to be deployed on all app servers in Stratos DC on a set schedule. Before that they need to test similar functionality with a sample cron job. Therefore, perform the steps below:

Install cronie package on all Nautilus app servers and start crond service.
Add a cron */5 * * * * echo hello > /tmp/cron_text for root user.

## Solution

```bash
sudo yum install cronie -y
sudo systemctl enable crond
sudo systemctl start crond
echo "*/5 * * * * echo hello > /tmp/cron_text" | sudo crontab -
```
