# manual-vm-setup
# Manual Multi-VM Application Deployment using Vagrant

## 📌 Project Overview
This project demonstrates a **manual deployment of a multi-tier Java web application** using multiple virtual machines. Each core service runs on a dedicated VM to closely simulate a real-world production environment. The setup focuses on service dependency management, internal networking, and application deployment using Vagrant and VirtualBox.

---

## 🏗️ Architecture Overview
The application follows a **multi-tier architecture**, where each tier is deployed on its own virtual machine.

### Services Used
| Service | Description | VM Name |
|------|------------|--------|
| Nginx | Web server & reverse proxy | web01 |
| Tomcat | Java application server | app01 |
| RabbitMQ | Message broker | rmq01 |
| Memcached | Database caching | mc01 |
| MySQL (MariaDB) | Relational database | db01 |

### Request Flow
User → Nginx → Tomcat → Database / Cache / Message Queue

## 🛠️ Technologies Used
- Vagrant
- Oracle VirtualBox
- Linux (CentOS / Ubuntu)
- Nginx
- Apache Tomcat
- MySQL (MariaDB)
- RabbitMQ
- Memcached
- Java 17
- Maven

## 📁 Project Structure
vprofile-manual-vm-setup
├── README.md
│
├── vagrant
│   └── Manual_provisioning
│       └── Vagrantfile
│
├── scripts
│   ├── mysql-setup.md
│   ├── memcache-setup.md
│   ├── rabbitmq-setup.md
│   ├── tomcat-setup.md
│   └── nginx-setup.md
│
└── docs
    ├── architecture.md
    ├── service-order.md
    └── access-info.md

yaml
Copy code


## ✅ Prerequisites
Ensure the following tools are installed on your system:
- Oracle VM VirtualBox
- Vagrant
- Git
- Git Bash or terminal

Install the required Vagrant plugin:
```bash
vagrant plugin install vagrant-hostmanager
