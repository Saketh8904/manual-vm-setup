```md

📁 docs/



==============================

📄 architecture.md

==============================



\# Project Architecture



\## Overview

This project follows a \*\*multi-tier architecture\*\*, where each service is deployed on a dedicated virtual machine. The design closely resembles a real-world production setup with clear separation of concerns.



\## Architecture Components



\- \*\*Web Layer\*\*  

&nbsp; - Service: Nginx  

&nbsp; - VM: web01  

&nbsp; - Role: Entry point and reverse proxy



\- \*\*Application Layer\*\*  

&nbsp; - Service: Apache Tomcat  

&nbsp; - VM: app01  

&nbsp; - Role: Hosts and executes the Java web application



\- \*\*Database Layer\*\*  

&nbsp; - Service: MySQL (MariaDB)  

&nbsp; - VM: db01  

&nbsp; - Role: Persistent data storage



\- \*\*Caching Layer\*\*  

&nbsp; - Service: Memcached  

&nbsp; - VM: mc01  

&nbsp; - Role: Reduces database load



\- \*\*Messaging Layer\*\*  

&nbsp; - Service: RabbitMQ  

&nbsp; - VM: rmq01  

&nbsp; - Role: Asynchronous message handling



\## Request Flow



User → Nginx (web01) → Tomcat (app01) → Database / Cache / Queue



\## Key Design Principles

\- Service isolation

\- Internal hostname-based communication

\- Manual provisioning to simulate real infrastructure

\- Easy debugging and observability





