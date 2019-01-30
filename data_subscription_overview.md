# Data Subscription Overview
EnOS System provides data subscription service to improve the API calling efficiency of applications with active data push, which supports subscription to real-time asset data, asset alert data, and asset meta data. Benefiting from the data subscription service, applications do not need to call APIs repeatedly and frequently to get asset data. Instead, applications call APIs only when there are pushed data, thus improving API calling efficiency and reducing costs.

## Features
- **Multiple data source subscription**: Data subscription service supports multiple data sources such as real-time asset data, asset alert data, etc.
- **Visualized configuration**: A GUI is available for users to customize the data subscription configuration, such as creating, configuring, starting, stopping, or deleting subscription topics.
- **Data subscription SDK**: Java SDK is provided for application developers to consume subscribed data.

## Advantages
- Decoupling data production and data consumption
- Rich set of data filtering conditions
- Cross-organization data subscription
- Supporting "at-least-once" message delivery semantics
- "Pulling subscribed data" consumption model, supporting traffic control of the client
- Supporting consumer groups (a topic can be consumed by multiple consumers repeatedly)

## Usage Limit
- At most 5 subscription topics are supported for an organization.
- Each topic has 2 partitions, that is, each topic allows at most 2 consumers at the same time.
- Currently, a consumer can consume 1 topic only.
- By default, data are stored in the topic for 3 days.



## Terminology

To help you understand data subscription related concepts and use the data subscription service to develop applications, definition and description of terms are as follows.

**Kafka**

Kafka is a distributed messaging system, which receives streams of data from the data producers and stores the data in categories called topics. Data consumers can simply read the stored data when needed, thus realizing asynchronous non-blocking I/O.

**Topic**

Message topic, which categorizes messages and stores received data streams.

**Partition**

Data saved in a topic are divided into partitions with specific logic. Partitions determine the number of producers or consumers who can write and read data in the topic. For example, if a topic has 3 partitions, the producer can start 3 processes to write data in the topic, and the consumer can have 3 processes to read data from the topic.

**Producer**

Message producer, also called message publisher.

**Consumer**

Message consumer, also called message subscriber.

**Consumer Group**

A group of consumers who can receive and consume the same messages with the same logic.

**Consumer Instance**

An object instance of consumer. Different consumer instances can run different processes or be run on different servers. Thread pools are configured for a consumer instance to consume messages. 

**Group Consumption**

All the consumer instances in a consumer group can consume messages in a topic averagely. For example, a topic has 9 messages, and a consumer group has 3 consumer instances, then a consumer instance can consume 3 messages in the group consumption mode.

**Sequential Publish**

For a specific topic, the client server publishes messages in a sequential order.

**Sequential Consumption**

For a specific topic, messages are received in a sequential order. That is, the message sent first must be received by the client first.

**Message Pileup**

Data producer sends messages to the subscription service, but the consumer fails to consume all the messages within a specific time because of limited capability. The messages not being consumed are saved in the subscription service, which is called message pileup.

**Message Filtering**

Subscriber can filter messages with specific conditions so as to receive filtered data only. Message filters can be configured in the subscription service.