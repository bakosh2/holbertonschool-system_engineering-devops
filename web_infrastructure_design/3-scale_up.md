<img height="50px" align="right" src="https://apply.holbertonschool.com/holberton-logo.png">

# Scale up

## Description

This is the diagram of a multi-server web infrastructure that hosts the website that is reachable via `www.mabat.com`.
It must be secured, serve encrypted traffic, and be monitored, while supporting Mabat's growth in users and bookings.

It contains two load balancers (HAProxy) configured as a cluster, two global servers, each with one web server (NGINX), one application server, and application files (Mabat's code base). The database layer is split into a Primary-Replica (Master-Slave) cluster, with the Primary handling all booking writes and the Replica handling all read traffic, such as browsing resorts.

## Diagram

<img align="center" src="https://raw.githubusercontent.com/bakosh2/holbertonschool-system_engineering-devops/main/web_infrastructure_design/assets/3-scale_up.png">

## Specifics about this infrastructure

- **Why add load balancers as a cluster?**

    Two load balancers are configured as a cluster for redundancy and high availability. If one load balancer fails — for example, during a traffic surge in summer — the other can seamlessly take over, ensuring Mabat stays online without interrupting active bookings.

- **Why separate the database into Primary and Replica?**

    Splitting the database into a Primary-Replica cluster allows write-heavy operations (new bookings, payments) to be isolated from read-heavy operations (browsing resorts, searching by city). This improves performance under load and removes the single database instance as a bottleneck.

- **Why separate components onto individual servers?**

    Splitting the web server, application server, and database onto separate, redundant servers improves resource management and isolation. It enhances security, performance, and scalability, and simplifies troubleshooting since each layer can be monitored and maintained independently.

This design improves the overall infrastructure's flexibility and reliability, which is particularly useful for Mabat as it scales to handle seasonal spikes in bookings. The load balancer cluster ensures that traffic is evenly distributed and provides resilience against load balancer failures, while the database cluster ensures booking data stays consistent and available even under heavy read traffic.
