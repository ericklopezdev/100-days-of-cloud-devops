# Day 11 - Install And Setup Tomcat Server

## Context

The Nautilus application development team recently finished the beta version of one of their Java-based applications, which they are planning to deploy on one of the app servers in Stratos DC. After an internal team meeting, they have decided to use the tomcat application server. Based on the requirements mentioned below complete the task:

Install tomcat server on App Server 1.
Configure it to run on port 8086.
There is a ROOT.war file on Jump host at location /tmp.
Deploy it on this tomcat server and make sure the webpage works directly on base URL i.e curl http://stapp01:8086

## Solution

```bash
sudo yum install java-1.8.0-openjdk-devel -y
sudo groupadd tomcat
sudo useradd -M -U -d /opt/tomcat -s /bin/nologin -g tomcat tomcat
sudo mkdir /opt/tomcat
wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.80/bin/apache-tomcat-9.0.80.tar.gz
sudo tar -xf apache-tomcat-9.0.80.tar.gz -C /opt/tomcat --strip-components=1
sudo chown -R tomcat:tomcat /opt/tomcat
# Create systemd service file with the content
sudo systemctl daemon-reload
sudo systemctl enable tomcat
sudo systemctl start tomcat
# Change port in server.xml to 8086
sudo mv /opt/tomcat/webapps/ROOT /opt/tomcat/webapps/ROOT.bak
scp /tmp/ROOT.war tony@stapp01:/home/tony/
unzip /home/tony/ROOT.war -d /opt/tomcat/webapps/ROOT
sudo systemctl restart tomcat
```
