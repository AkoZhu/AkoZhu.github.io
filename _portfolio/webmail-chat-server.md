---
title: "Webmail and Chat system"
date: 2024-03-09
excerpt: "Built the distributed webmail system and chat system. <br/><img src='/images/portforlio/webmail-chat-server/webmail-diagram.png' width='60%'>"
location: "University of Pennsylvania"
collection: portfolio
---

I built a webmail system and chat room system separately, with different architecture for different purpose. 

# Components

## Webmail System
<p align="center">
  <img src="/images/portforlio/webmail-chat-server/webmail-diagram.png">
</p>
I designed and developed a comprehensive email service on a Linux VM using C++, TCP/IP, and a multi-thread server architecture with a thread pool.
- **Service Functionality**: This service supports both *SMTP* and *POP3* protocols, enabling robust and concurrent email transactions from clients such as *Thunderbird*. The SMTP server handles email sending functions. And the POP3 server manages emial retrieval. The server handles various emial operations in SMTP and POP3, including user authentication, message storage and retrieval.
- **Design Decision**: 
  - **Multi-thread server**: Handled multiple clients' connections at the same time without performance degradation.
  - **Thread Pool**: To reuse the thread resource and avoid overhead, optimizing CPU utilization and response time. 


## Chat System
<p align="center">
  <img src="/images/portforlio/webmail-chat-server/chat-server-diagram.png">
</p>

I designed and crafted a high-performance chat server on a *Linux VM* using *C++, UDP, and an event-driven, multiplexed I/O design*. The service supports over 50 servers and 900+ clients.
- **Service Functionality**: This service allows clients to join chat rooms and exchange messages in chat room, with the server s using multicast to distribute messages to other servers, which then forward them to the clients in the appropriate chat rooms. 
- **Multicast Protocol**: Implemented the advanced multicast group communication in chat service, making a robust message delivery across various message ordering protocol, including *Unordered, FIFO, Causal, and Total Ordering*. These protocol implementation significantly improves the reliability and user experience, even in challenging network condition(Loss or Large Delay). The design of Multicast and different ordering protocol ensure that messages are delivered to the whole group(Chat room) consitently and predictably, making a robust and scalable chat service. 
- **Event-driven and Multiplexed I/O design**: Implemented the Event-driven and Multiplexed I/O design to achive the high throughput and low context switching, efficiently managing network I/O.
  