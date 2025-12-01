```md

📁 docs/



==============================

📄 access-info.md

==============================



\# Access Information



\## Application Access



After successful setup, access the application using:



\- \*\*URL (Browser):\*\*

&nbsp; ```

&nbsp; http://<web01-ip>

&nbsp; ```



Or, if hostname resolution is available:

```

http://web01

```



\## Default Credentials



\- \*\*Username:\*\* admin  

\- \*\*Password:\*\* admin123



\## Service Ports



| Service     | VM     | Port  |

|------------|--------|-------|

| Nginx      | web01  | 80    |

| Tomcat     | app01  | 8080  |

| MySQL      | db01   | 3306  |

| Memcached  | mc01   | 11211 |

| RabbitMQ   | rmq01  | 5672  |



\## SSH Access



```bash

vagrant ssh <vm-name>

```



Example:

```bash

vagrant ssh app01

```



\## Troubleshooting Tip

If the application does not load:

\- Verify Tomcat is running

\- Verify firewall rules

\- Test backend reachability using curl

\- Check Nginx logs



