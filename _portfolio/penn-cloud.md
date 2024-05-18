---
title: "Penn Cloud"
date: 2024-05-09
excerpt: "Built the Distributed Penn Cloud in a team of four. <br/><img src='/images/portforlio/web-search-engine/main-page.png'>"
location: "University of Pennsylvania"
collection: portfolio
---

_This is a course project for CIS505 Software Systems(Spring 2024) at University of Pennsylvania._

Our team built a Distributed Penn Cloud Application, supporting **User Service**, **Email Service**, **Drive Service**, and **Monitor Service**.

The diagram is as follows:
<p align="center">
  <img src="/images/portforlio/penn-cloud/diagram.jpeg">
</p>

# Components

## Key-Value Store
Our PennCloud application includes a robust key-value store inspired by Google's BigTable, featuring persistence, replication, and fault-tolerance. The system uses a master-slave archiecture with hashing slot and for data sharding, distributeing rows among replication groups. Each group consistes of one primary and two secondary nodes, maintaining strong consistency through sequentialized requests, centralized checkpointing, Append-Only File(AOF) logging and row-level locking. Fault tolerance is achieved by ensuring the system remains operational as long as at least one node in each replication group is alive. The system will only accept read if the previous condition is unsatisfied. 

## Frontend Server
The frontend of our PennCloud application is built using an MVC design, inspired by Spring framework, ensuring scalability and ease of maintaince. The web server handles HTTP requests, parses them, and dispatches them to appropriate handlers based on the request path and method. Authentication is implemented by the JWT in cookies, providing user isolation and management. The frontend supports various user interactions, including dynamic content loading and RESTful API design. The user interfaces for storage service and email service are built with Twilwind CSS.

## Webmail Service
The webmail service is designed to handle both internal and external emial communications. It includes an SMTP server to accept emails from within and outside the system and an SMTP client to send emails to local and remote users. The service contains web-based interface for managing mails, like viewing, composing, and deleting messages. Emails and metadata are stored in key-value store. 

## Web Storage Service
The web storage service mimics the functionality of Google Drive, allowing users to upload, download, and manage files and directories. It supports various functionalities, such as creating, moving, renaming, and deleting directories and files. Large files are chunked into  for storage, improving the fault-tolerance and load balancing. As for binary files, they will be encoded by BASE64 algorithm. A tree-like folder structure decouples the file structure from the actual data, enhancing the performance and scalability.

## Admin Console
The admin console is for monitoring and managing the PennCloud system. It provides real-time status updates of frontend and backend nodes, displaying whether they are alive or dead. The console allows administrators to start and stop backend nodes, view the key-value data inside the alive nodes, and manage the overall system health. The monitor is a two-layer architecture, the coordinators of frontend/backend utilize the Push-based strategy to gather information from worker nodes, and the monitor uses the Push-based strategy to gather information from both coordinators. 

## Load Balancer
The load balancer in PennCloud ensures efficient distribution of user requests to frontend nodes. Upon startup, frontend nodes register with the load balancer using the configure file. 
The load balancer redirect the incomming requests to available nodes based on round-robin and heal-based check. The load balancer also communicates with the admin console to report the status of the frontend nodes. 

Here is the report: [PorjectReport](/files/penn-cloud-report.pdf)

Some screenshots of our application:
<table>
  <tr>
    <td style="padding:10px;"><img src="/images/portforlio/penn-cloud/penn-cloud-screenshots/screenshot_1.png" width="100%"></td>
    <td style="padding:10px;"><img src="/images/portforlio/penn-cloud/penn-cloud-screenshots/screenshot_2.png" width="100%"></td>
  </tr>
  <tr>
    <td style="padding:10px;"><img src="/images/portforlio/penn-cloud/penn-cloud-screenshots/screenshot_3.png" width="100%"></td>
    <td style="padding:10px;"><img src="/images/portforlio/penn-cloud/penn-cloud-screenshots/screenshot_4.png" width="100%"></td>
  </tr>
</table>