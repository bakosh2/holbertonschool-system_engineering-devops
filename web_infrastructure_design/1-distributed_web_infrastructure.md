<img height="50px" align="right" src="https://apply.holbertonschool.com/holberton-logo.png">

# Distributed web infrastructure

## Description

This is the diagram of a three server web infrastructure that hosts the website that is reachable via `www.mabat.sa`.

It contains one load-balancer (HAProxy), two global servers, each with one web server (NGINX), one application server, application files (Mabat's code base) and one shared database (MySQL).

## Diagram

<img align="center" src="https://raw.githubusercontent.com/bakosh2/holbertonschool-system_engineering-devops/main/web_infrastructure_design/assets/1-distributed_web_infrastructure.png">

## Specifics about this infrastructure

- **Why add a load-balancer?**

    Adding a load-balancer distributes incoming traffic evenly across multiple application servers. This provides redundancy and ensures high availability. If Mabat experiences a spike in bookings (e.g., during summer season) and one server fails, the load balancer routes traffic to the remaining healthy server.

- **What distribution algorithm is your load balancer configured with and how does it work?**

    The load-balancer is configured with a Round Robin distribution algorithm. It works by sequentially forwarding each new request to the next server in line, distributing the load evenly between the two servers.

- **Is your load-balancer enabling an Active-Active or Active-Passive setup?**

    The load balancer enables an Active-Active setup. Both servers are actively processing requests simultaneously. In an Active-Passive setup, one server would be active while the other stays on standby, only becoming active if the primary server fails.

- **How does a database Primary-Replica (Master-Slave) cluster work?**

    In this configuration, the Primary node is the master database that handles write operations (INSERT, UPDATE, DELETE) such as new bookings, while the Replica node(s) replicate data from the Primary. Read operations, like browsing resort listings, can be distributed to Replicas.

- **What is the difference between the Primary node and the Replica node in regard to the application?**

    The Primary node is responsible for handling write operations and maintaining the authoritative copy of Mabat's data. The Replica nodes copy data from the Primary and are used for read operations, reducing the load on the Primary and providing data redundancy.

## Issues with this infrastructure

- The load-balancer can become a SPOF (Single Point Of Failure) if it fails. To address this, a redundant load-balancer can be implemented.

- The absence of a firewall poses a security risk, as it doesn't protect Mabat's infrastructure from unauthorized access or attacks.

- Lack of HTTPS leaves the infrastructure vulnerable to data interception and tampering during transmission, especially concerning since Mabat will process online payments.

- The infrastructure lacks monitoring, making it challenging to detect and respond to issues proactively. Monitoring tools should be implemented to ensure the system's health and performance.

- The database is not distributed yet — it remains a single, shared instance, which is still a SPOF for both servers.
