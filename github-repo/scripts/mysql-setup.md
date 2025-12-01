📁 scripts/mysql-setup.md

\# MySQL (MariaDB) Setup



\## VM Details

\- \*\*VM Name:\*\* db01

\- \*\*Service:\*\* MySQL (MariaDB)

\- \*\*Port:\*\* 3306



\## Purpose

Provides persistent relational data storage for the application.



---



\## Setup Steps



\### 1. Login to DB VM

```bash

vagrant ssh db01



2\. Update System

sudo dnf update -y

sudo dnf install epel-release -y



3\. Install MariaDB

sudo dnf install mariadb-server git -y



4\. Start and Enable Service

sudo systemctl start mariadb

sudo systemctl enable mariadb



5\. Secure Database

sudo mysql\_secure\_installation





Set root password and remove test/anonymous users.



Database Initialization

6\. Create Database and User

mysql -u root -p



CREATE DATABASE accounts;

GRANT ALL PRIVILEGES ON accounts.\* TO 'admin'@'localhost' IDENTIFIED BY 'admin123';

GRANT ALL PRIVILEGES ON accounts.\* TO 'admin'@'%' IDENTIFIED BY 'admin123';

FLUSH PRIVILEGES;

EXIT;



7\. Import Schema

git clone https://github.com/hkhcoder/vprofile-project.git

mysql -u root -p accounts < vprofile-project/src/main/resources/db\_backup.sql



Firewall Configuration

sudo systemctl start firewalld

sudo firewall-cmd --add-port=3306/tcp --permanent

sudo firewall-cmd --reload



Verification

systemctl status mariadb

