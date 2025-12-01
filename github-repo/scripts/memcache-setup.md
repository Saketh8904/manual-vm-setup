---



\# 📁 `scripts/memcache-setup.md`



```md

\# Memcached Setup



\## VM Details

\- \*\*VM Name:\*\* mc01

\- \*\*Service:\*\* Memcached

\- \*\*Port:\*\* 11211



\## Purpose

Reduces database load by caching frequently accessed data.



---



\## Setup Steps



\### 1. Login to VM

```bash

vagrant ssh mc01

2\. Install Memcached

bash

Copy code

sudo dnf update -y

sudo dnf install epel-release memcached -y

3\. Configure Service

bash

Copy code

sudo sed -i 's/127.0.0.1/0.0.0.0/' /etc/sysconfig/memcached

4\. Start and Enable

bash

Copy code

sudo systemctl start memcached

sudo systemctl enable memcached

Firewall Configuration

bash

Copy code

sudo systemctl start firewalld

sudo firewall-cmd --add-port=11211/tcp --permanent

sudo firewall-cmd --reload

Verification

bash

Copy code

systemctl status memcached

