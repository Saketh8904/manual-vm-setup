\# 📁 `scripts/nginx-setup.md`



```md

\# Nginx Setup



\## VM Details

\- \*\*VM Name:\*\* web01

\- \*\*Service:\*\* Nginx

\- \*\*Port:\*\* 80



\## Purpose

Acts as a reverse proxy and entry point for the application.



---



\## Setup Steps



\### 1. Login to VM

```bash

vagrant ssh web01

sudo -i

2\. Install Nginx

bash

sudo apt update

sudo apt install nginx -y

Configure Reverse Proxy

Create config:



bash

sudo vim /etc/nginx/sites-available/vproapp

nginx

Copy code

upstream vproapp {

&nbsp;   server app01:8080;

}



server {

&nbsp;   listen 80;

&nbsp;   location / {

&nbsp;       proxy\_pass http://vproapp;

&nbsp;   }

}

Enable Site:



bash

sudo rm /etc/nginx/sites-enabled/default

sudo ln -s /etc/nginx/sites-available/vproapp /etc/nginx/sites-enabled/vproapp

Restart \& Verify

bash

Copy code

sudo nginx -t

sudo systemctl restart nginx

