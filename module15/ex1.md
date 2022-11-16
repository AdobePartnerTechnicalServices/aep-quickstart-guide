---
title: Introduction to Apache Kafka
description: Introduction to Apache Kafka
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 7b600c79-03c5-46fc-9ac9-a15599608c35
---
# 15.1 Introduction to Apache Kafka

## 15.1.1 Introduction

Every organization starts off in a very simple way from a data perspective. An organization's data ecosystem starts with one source system and one target. The source system sends data to the target system, and that's it. Easy, right?
If only it would remain that simple. Organizations quickly outgrow that simple setup and the number of source systems and target systems quickly increases. All these different sources and destinations need to exchange data with eachother, and things quickly become very complex.
For instance, if an organization has 4 sourcs and 6 destinations and all these applications need to speak with eachother, you'll need to build 24 integrations... Each of those integrations comes with its own difficulties:

- protocol: how is data transported (TCP, HTTP, REST, FTP, ...)
- data format: how is the data parsed (binary, CSV, JSON, Parquet, ...)
- data schema and evolution: what is the data model and how will it evolve?

Additionally, each time you connect a source system to a destination system, there'll be an increased load on those systems from that connection.

So, how do you solve this? That's where Apache Kafka comes into the picture. Apache Kafka allows an organization to decouple data streams and systems by providing a commo, high-throughput, distributed messaging system. Source systems will send their data into Apache Kafka, and destination systems will consume data from Apache Kafka.

Think of all the types of data sources experience businesses have to manage:

- website events
- mobile app events
- POS events
- CRM data
- callcenter data
- transaction history
- ...

And think of all the types of destinations experience businesses use in their ecosystem which all might need data from those source systems:

- CRM
- data lake
- email system
- audit
- analytics
- ...

Apache Kafka was created by LinkedIn and is now an open source project mainly maintained by Confluent.
Apache Kafka provides a distributed, resilient architecture that is fault tolerant. It can scale horizontally to 100s of brokers and can scale to millions of messages per second. It provides a high performance with latencies of less than 10ms which is ideal for real-time use cases.

A couple of use case examples:

- Messaging System
- Activity Tracking
- Gather metrics from many different locations
- Application logs gathering
- Stream processing (with Kafka Streams API or Spark)
- Decoupling of system dependencies
- Integration with Spark, Flink, Storm, Hadoop and many other Big Data technologies.

For instance:

- Netflix uses Kafka to apply recommendations in real-time while you're watching TV shows
- Uber uses Kafka to gather user, taxi and trip data in real-time to compute and forecast demand and compute surge pricing in real-time
- LinkedIn uses Kafka to prevent spam, collect user interactions to make better connection recommendations in real-time

For all these use cases, Kafka is only used as a transportation mechanism. Kafka is really good at moving data between applications.

## 15.1.2 Kafka Terminology

### Message

A message is a communication sent by a system into Kafka. A message contains a payload, and a payload contains data elements. For instance, an experience event sent by a website into Adobe Experience Platform is considered as a message.

### Topic, partitions, offsets

A topic is a particular stream of data, similar to a table in a database. You can have as many topics as you want, and a topic is identified by its name. Topics are split in partitions. Each partition is ordered and each message within a partition gets an incremental id, which is called **offset**. Messages are stored in a topic, on a partition and is referenced using an offset. Messages are kept only for a limited time (default is 1 week). Once a message is written to a partition, it can't be changed anymore.

### Brokers

A broker is similar to a server. A Kafka cluster is composed of multiple brokers (servers). Each broker is identified with an ID and contains certain topic partitions.

### Replication

Kafka is a distributed system. One of the important things of a distributed system is that data is securely stored and as such, replication is needed. After all, when one broker (server) goes down, another broker (server) should still be able to provide access to messages that were initially stored on the broker that went down. Replication will create copies of messages across multiple brokers to guarantee that no data is lost.

### Producers

How is data sent to Kafka? That's the role of a producer. A producer connects to a source system and takes data from the source system, and then writes that data to topics onto partitions. Based on the configuration of your Kafka cluster, producers will automatically know which broker and partition to write to. In a distributed system with multiple brokers and replication strategy, a producer will store data randomly across multiple brokers, which means that it will do load balancing automatically.

### Message keys

Producers can choose to send a key with the message. A key can be any string, number, etc. If no key is provided, a message will be sent randomly to brokers. If a key is sent, then all messages for that key will always go to the same partition. A message key as such is used to order messages based on a specific field.

### Consumers

Consumers read data from an Apache Kafka topic and then share that data with destination systems. Consumers know which broker to read from. Data is read by a consumer in order, within each partition. Consumers read data in consumer groups.

### Zookeeper

ZooKeeper is essentially a service for distributed systems offering a hierarchical key-value store, which is used to provide a distributed configuration service, synchronization service, and naming registry for large distributed systems. Zookeeper needs to be running before you can use Apache Kafka, and Zookeeper is sort of the master of ceremony for Kafka, managing distributed services in the backend while Kafka produces and consumes events.

You have finished this exercise.
