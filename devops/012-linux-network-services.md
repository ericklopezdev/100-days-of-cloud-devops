# Day 12 - Linux Network Services

## Context

Our monitoring tool has reported an issue in Stratos Datacenter. One of our app servers has an issue, as its Apache service is not reachable on port 3000 (which is the Apache port). The service itself could be down, the firewall could be at fault, or something else could be causing the issue.

Use tools like telnet, netstat, etc. to find and fix the issue. Also make sure Apache is reachable from the jump host without compromising any security settings.

Once fixed, you can test the same using command curl http://stapp01:3000 command from jump host.


## Solution
```bash
sudo netstat -tlnup
cd /etc/mail
vi sendmail.mc  # Change DAEMON_OPTIONS Port to 1234
sudo systemctl restart sendmail
sudo iptables -I INPUT 4 -p tcp --dport 3000 -j ACCEPT
curl http://localhost:3000
curl http://stapp01:3000
```
