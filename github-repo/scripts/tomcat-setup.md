---



\# 📁 `scripts/tomcat-setup.md`



```md

\# Tomcat Application Server Setup



\## VM Details

\- \*\*VM Name:\*\* app01

\- \*\*Service:\*\* Apache Tomcat

\- \*\*Port:\*\* 8080



\## Purpose

Hosts and runs the Java web application.



---



\## Setup Steps



\### 1. Login to VM

```bash

vagrant ssh app01

2\. Install Dependencies

bash

sudo dnf update -y

sudo dnf install epel-release java-17-openjdk java-17-openjdk-devel git wget unzip -y

3\. Install Tomcat

bash


cd /tmp

wget https://archive.apache.org/dist/tomcat/tomcat-10/v10.1.26/bin/apache-tomcat-10.1.26.tar.gz

tar xzf apache-tomcat-10.1.26.tar.gz

sudo useradd -r tomcat

sudo mkdir /usr/local/tomcat

sudo cp -r apache-tomcat-10.1.26/\* /usr/local/tomcat

sudo chown -R tomcat:tomcat /usr/local/tomcat

Create Systemd Service

Create /etc/systemd/system/tomcat.service:

ini


\[Unit]

Description=Tomcat

After=network.target



\[Service]

User=tomcat

Group=tomcat

WorkingDirectory=/usr/local/tomcat

Environment=JAVA\_HOME=/usr/lib/jvm/jre

ExecStart=/usr/local/tomcat/bin/catalina.sh run

ExecStop=/usr/local/tomcat/bin/shutdown.sh

Restart=always



\[Install]

WantedBy=multi-user.target

Enable Service

bash

sudo systemctl daemon-reload

sudo systemctl start tomcat

sudo systemctl enable tomcat

Firewall Configuration

bash

sudo firewall-cmd --add-port=8080/tcp --permanent

sudo firewall-cmd --reload

