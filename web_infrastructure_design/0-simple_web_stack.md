<img height="50px" align="right" src="https://apply.holbertonschool.com/holberton-logo.png">

# Simple web stack

## Description

This is the diagram of a one server web infrastructure that hosts the website that is reachable via `www.mabat.com`.

It contains one global server (IP: 8.8.8.8) with one web server (NGINX), one application server, application files (Mabat's code base) and one database (MySQL).

## Diagram

<img align="center" src="https://raw.githubusercontent.com/bakosh2/holbertonschool-system_engineering-devops/main/web_infrastructure_design/assets/0-simple_web_stack.png">

## Specifics about this infrastructure

- **What is a server?**

    It's a computer or system responsible for providing services, resources, or data to other computers, known as clients, over a network. In this case, it hosts the website for `www.mabat.com`.

- **What is the role of the domain name?**

    `mabat.com` is a human-readable address that allows divers and travelers to access the website. It acts as a user-friendly reference to the server's IP address.

- **What type of DNS record `www` is in `www.mabat.com`?**

    The "www" is typically a CNAME (Canonical Name) DNS record, which is an alias for the domain name, directing it to the server's IP address.

- **What is the role of the web server?**

    The web server (NGINX) handles incoming HTTP requests from users' browsers. It serves static content, like HTML and CSS files, and forwards dynamic requests (such as browsing coastal resorts or submitting a booking) to the application server.

- **What is the role of the application server?**

    It runs Mabat's application code and processes dynamic requests, such as searching for resorts by city or handling a booking request.

- **What is the role of the database?**

    The MySQL database stores and manages Mabat's data, such as user accounts, resort listings, bookings, and reviews, which the application server accesses and modifies.

- **What is the server using to communicate with the computer of the user requesting the website?**

    The server communicates with the user's computer over the internet using the HTTP protocol, which is the standard for web communication. It sends and receives HTTP requests and responses.

## Issues with this infrastructure

- There are multiple SPOF (Single Point Of Failure) in this web infrastructure.
For example, if the application server or the database is down, the entire Mabat website would be down.

- When updates or maintenance are needed, the web server may need to be restarted, causing downtime for users during that period.

- This infrastructure cannot easily handle a sudden increase in traffic, such as a surge in bookings during summer season. To scale, additional servers and load balancing mechanisms would be required.
