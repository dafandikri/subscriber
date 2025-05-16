# Software Architectures Tutorial Reflection

This document reflects on Software Architectures

## Reflection 1

### a. What is amqp?

AMQP stands for Advanced Message Queuing Protocol. It is an open standard application layer protocol for message-oriented middleware. AMQP enables systems to communicate by sending messages between clients and servers, supporting reliable queuing, routing, security, and message delivery guarantees. It is commonly used in distributed systems and microservices architectures for decoupling components and ensuring reliable communication.

### b. What does it mean? guest:guest@localhost:5672

- The first 'guest' is the username used to authenticate with the AMQP server (such as RabbitMQ).
- The second 'guest' is the password for the username.
- 'localhost' refers to the local machine (the AMQP server is running on the same computer).
- '5672' is the default port number for AMQP protocol communication.

So, 'amqp://guest:guest@localhost:5672' is a connection string that tells the client to connect to an AMQP server running locally, using the username 'guest' and password 'guest', on port 5672.

# Simulating Slow Subscriber

![RabbitMQ Queue Simulation](simulating_slow.png)

## Why is the total number of queue messages as such?

The total number of messages in the queue reflects how many messages were published by the publisher while the subscriber was still processing previous messages. Since the subscriber processes each message with a 1-second delay, but the publisher can send messages much faster, the queue grows quickly. The total number in my case is 30. This number depends on how many times the publisher was run quickly and how many messages each run sent before the subscriber could catch up. The queue will decrease slowly as the subscriber processes each message one by one.

# Running Multiple Subscribers

![Three Subscribers Processing](three_subscribers.png)

## Reflection

When running three subscriber instances, the message queue in RabbitMQ is drained much faster compared to running only one. This is because each subscriber pulls messages from the queue and processes them in parallel, splitting the workload. In my test, I observed that the messages were distributed among the subscribers, and the queue spike was reduced more quickly.

This demonstrates the scalability of event-driven architectures: by adding more consumers, we can handle higher loads and prevent message backlog.

### Possible Improvements

- Implement better error handling and logging in both publisher and subscriber.
- Allow dynamic scaling of subscribers based on queue length.
- Graceful shutdown for subscribers to finish processing current messages before exiting.
