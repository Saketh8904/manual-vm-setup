\# 📁 `scripts/rabbitmq-setup.md`



```md

\# RabbitMQ Setup



\## VM Details

\- \*\*VM Name:\*\* rmq01

\- \*\*Service:\*\* RabbitMQ

\- \*\*Port:\*\* 5672



\## Purpose

Handles asynchronous messaging between application components.



---



\## Setup Steps



\### 1. Login to VM

```bash

vagrant ssh rmq01

2\. Install Dependencies

bash

Copy code

sudo dnf update -y

sudo dnf install epel-release wget -y

3\. Install RabbitMQ

bash

sudo dnf install centos-release-rabbitmq-38 -y

sudo dnf --enablerepo=centos-rabbitmq-38 install rabbitmq-server -y

4\. Start and Enable

bash

sudo systemctl start rabbitmq-server

sudo systemctl enable rabbitmq-server

User Configuration

bash


sudo rabbitmqctl add\_user test test

sudo rabbitmqctl set\_user\_tags test administrator

sudo rabbitmqctl set\_permissions -p / test ".\*" ".\*" ".\*"

Allow remote access:



bash


echo "\[{rabbit, \[{loopback\_users, \[]}]}]." | sudo tee /etc/rabbitmq/rabbitmq.config

sudo systemctl restart rabbitmq-server

Firewall Configuration

bash


sudo firewall-cmd --add-port=5672/tcp --permanent

sudo firewall-cmd --reload

