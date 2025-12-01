```md

📁 docs/


==============================

📄 service-order.md

==============================



\# Service Provisioning Order



\## Why Order Matters

Each service depends on others being available. To avoid runtime and connectivity failures, services must be set up in a specific order.



\## Correct Setup Sequence



1\. \*\*MySQL (db01)\*\*  

&nbsp;  Foundation service for data storage.



2\. \*\*Memcached (mc01)\*\*  

&nbsp;  Depends on database configuration.



3\. \*\*RabbitMQ (rmq01)\*\*  

&nbsp;  Required before application startup.



4\. \*\*Tomcat (app01)\*\*  

&nbsp;  Requires all backend services to be reachable.



5\. \*\*Nginx (web01)\*\*  

&nbsp;  Final entry point; proxies traffic to Tomcat.



\## Consequences of Wrong Order

\- Application startup failures

\- Connection refused errors

\- 502 Bad Gateway from Nginx

\- Backend service crashes



\## Best Practice

Always verify each service is:

\- Running

\- Enabled at boot

\- Reachable via hostname and port  

before proceeding to the next.



