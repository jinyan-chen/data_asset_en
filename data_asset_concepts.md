# Concepts

This topic introduces the major concepts involved in data asset management.

## About Stream Data Analytics

The major concepts include stream data, stream analytics, data type, and data processing strategy. For details about these concepts, see [Stream Data Analytics Concepts](https://www.envisioniot.com/docs/online-data/en/latest/streaming_concept.html).

## About Data Subscription

To help you understand data subscription related concepts and use the data subscription service to develop applications, definition and description of related terms are as follows.

### Kafka

Kafka is a distributed messaging system, which receives streams of data from the data producers and stores the data in categories called topics. Data consumers can simply read the stored data when needed, thus realizing asynchronous non-blocking I/O.

### Topic

Message topic, which categorizes messages and stores received data streams.

### Partition

Data saved in a topic are divided into partitions with specific logic. Partitions determine the number of producers or consumers who can write and read data in the topic. For example, if a topic has 3 partitions, the producer can start 3 processes to write data in the topic, and the consumer can have 3 processes to read data from the topic.

### Data producer

A data producer is the device that uploads data to EnOS Cloud. A data producer is also called a message publisher.

### Data consumer

A data consumer is the data subscriber. A consumer group is a collection of consumers who can receive and consume the same messages with the same logic.

### Consumer instance

An object instance of consumer. Different consumer instances can run different processes or be run on different servers. Thread pools are configured for a consumer instance to consume messages.

### Group consumption

All the consumer instances in a consumer group can consume messages in a topic averagely. For example, a topic has 9 messages, and a consumer group has 3 consumer instances, then a consumer instance can consume 3 messages in the group consumption mode.

### Sequential publish

For a specific topic, the client server publishes messages in a sequential order.

### Sequential consumption

For a specific topic, messages are received in a sequential order. That is, the message sent first must be received by the client first.

### Message pileup

Data producer sends messages to the subscription service, but the consumer fails to consume all the messages within a specific time because of limited capability. The messages not being consumed are saved in the subscription service, which is called message pileup.

### Message Filtering

Subscriber can filter messages with specific conditions so as to receive filtered data only. Message filters can be configured in the subscription service.

<!--

## About Storage Policy

To help you understand data storage policy related concepts and customize data storage policies, definition and description of related terms are as follows.

**Storage group**

A storage group is

**Storage type**

A storage type is

-->
