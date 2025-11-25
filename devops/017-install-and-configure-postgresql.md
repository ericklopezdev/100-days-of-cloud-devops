# Day 17 - Install And Configure Postgresql

## Context
The Nautilus application development team has shared that they are planning to deploy one newly developed application on Nautilus infra in Stratos DC. The application uses PostgreSQL database, so as a pre-requisite we need to set up PostgreSQL database server as per requirements shared below:

PostgreSQL database server is already installed on the Nautilus database server.

Create a database user kodekloud_aim and set its password to your-password.
Create a database kodekloud_db6 and grant full permissions to user kodekloud_aim on this database.
Please do not try to restart PostgreSQL server service.

## Solution
```bash
sudo -i -u postgres
psql -c "CREATE DATABASE kodekloud_db6;"
psql -c "CREATE ROLE kodekloud_aim LOGIN PASSWORD 'your-password';"
psql -c "GRANT ALL PRIVILEGES ON DATABASE kodekloud_db6 TO kodekloud_aim;"
psql -c "ALTER DATABASE kodekloud_db6 OWNER TO kodekloud_aim;"
```
