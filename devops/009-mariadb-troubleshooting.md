# 009-mariadb-troubleshooting

## Context

There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.


## Solution

```bash
sudo chown -R mysql:mysql /var/lib/mysql
sudo systemctl start mariadb
```
