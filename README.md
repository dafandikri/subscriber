# gRPC Tutorial Reflection

This document reflects on Software Architectures

## Refelction 1

### a. What is amqp?

AMQP stands for Advanced Message Queuing Protocol. It is an open standard application layer protocol for message-oriented middleware. AMQP enables systems to communicate by sending messages between clients and servers, supporting reliable queuing, routing, security, and message delivery guarantees. It is commonly used in distributed systems and microservices architectures for decoupling components and ensuring reliable communication.

### b. What does it mean? guest:guest@localhost:5672

- The first 'guest' is the username used to authenticate with the AMQP server (such as RabbitMQ).
- The second 'guest' is the password for the username.
- 'localhost' refers to the local machine (the AMQP server is running on the same computer).
- '5672' is the default port number for AMQP protocol communication.

So, 'amqp://guest:guest@localhost:5672' is a connection string that tells the client to connect to an AMQP server running locally, using the username 'guest' and password 'guest', on port 5672.
