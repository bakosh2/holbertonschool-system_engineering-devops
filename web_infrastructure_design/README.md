<img height="50px" align="right" src="https://apply.holbertonschool.com/holberton-logo.png">

# Web infrastructure design

## Description

This project focuses on web infrastructure design, by creating diagrams and explaining the role of each component in a typical web stack.

All four diagrams in this project describe the infrastructure for `www.mabat.com`, a booking platform for coastal resorts in Saudi Arabia, as it evolves from a single server to a secured, monitored, and scaled multi-server setup.

## Objectives

At the end of this project, the goal is to be able to explain, without the help of Google:

- What a server is and what a web stack is made of.
- The role of a domain name and DNS records.
- The role of a web server, an application server, and a database.
- Why and how to add a load balancer.
- The difference between Active-Active and Active-Passive setups.
- Why and how to secure and monitor a web infrastructure.
- Why and how to set up a database cluster (Primary-Replica).
- How to identify a Single Point of Failure (SPOF) in a given infrastructure.

## Tasks

| # | Task | Diagram |
|---|---|---|
| 0 | [Simple web stack](./0-simple_web_stack.md) | One server hosting everything |
| 1 | [Distributed web infrastructure](./1-distributed_web_infrastructure.md) | Load balancer + 2 servers + shared database |
| 2 | [Secured and monitored web infrastructure](./2-secured_and_monitored_web_infrastructure.md) | Adds firewalls, HTTPS, and monitoring |
| 3 | [Scale up](./3-scale_up.md) | Clustered load balancers + Primary-Replica database |

[See all diagrams in one page](./all_for_one.md)

## Tech stack

- NGINX — web server
- MySQL — database
- HAProxy — load balancer
- SSL/TLS — encryption
- Firewalls & monitoring clients

## Author

**Ebtihal Alomari** — Holberton School
