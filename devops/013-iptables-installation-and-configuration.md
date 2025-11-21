# Day 13 - Iptables Installation And Configuration

## Context
We have one of our websites up and running on our Nautilus infrastructure in Stratos DC. Our security team has raised a concern that right now Apache’s port i.e 6200 is open for all since there is no firewall installed on these hosts. So we have decided to add some security layer for these hosts and after discussions and recommendations we have come up with the following requirements:

Install iptables and all its dependencies on each app host.
Block incoming port 6200 on all apps for everyone except for LBR host.
Make sure the rules remain, even after system reboot.

## Solution
```bash
sudo yum install -y iptables iptables-services
sudo iptables -A INPUT -p tcp --dport 6200 -s 172.16.238.14 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 6200 -j REJECT
sudo service iptables save
```
