# Day 16 - Install And Configure Nginx As Load Balancer

## Context
Day by day traffic is increasing on one of the websites managed by the Nautilus production support team. Therefore, the team has observed a degradation in website performance. Following discussions about this issue, the team has decided to deploy this application on a high availability stack i.e on Nautilus infra in Stratos DC. They started the migration last month and it is almost done, as only the LBR server configuration is pending. Configure LBR server as per the information given below:

Install nginx on LBR server
Configure load-balancing with the an http context making use of all App Servers. Ensure that you update only the main Nginx configuration file located at /etc/nginx/nginx.conf
Make sure you do not update the apache port that is already defined in the apache configuration on all app servers, also make sure apache server is up and running on all app servers
Once done, you can access the website using StaticApp button on the top bar

## Solution
```bash
sudo yum install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
sudo ss -tlnup  # Check app ports, e.g., 5001
sudo vi /etc/nginx/nginx.conf  # Add upstream stapp { server stapp01:5001; ... }, location / { proxy_pass http://stapp; ... }
sudo nginx -t
sudo systemctl restart nginx
```
