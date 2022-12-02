---
title: Stream data from Apache Kafka into Adobe Experience Platform
description: In this module, you'll learn how to setup your own Apache Kafka cluster, define topics, producers and consumers and stream data into Adobe Experience Platform using the Adobe Experience Platform Sink Connector for Kafka Connect.
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: e1e283b1-93b7-4d06-b9ed-beac48a99c3f
---
# 15. Stream data from Apache Kafka into Adobe Experience Platform

**Authors: [Vivek Tiwari](https://www.linkedin.com/in/vivek-tiwari-25092656/), [Nipun Nair](https://www.linkedin.com/in/nipunnair/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In this module, you'll learn how to setup your own Apache Kafka cluster, define topics, producers and consumers and stream data into Adobe Experience Platform using the Adobe Experience Platform Sink Connector through Kafka Connect.

## Learning Objectives

- Perform a basic setup of a local Kafka cluster
- Create a Kafka topic, use a Kafka producer and a Kafka consumer
- Configure Kafka Connect and the Adobe Experience Platform Sink Connector
- Manually produce events and see those events get ingested in Adobe Experience Platform
- Use an existing Twitter producer library from Kafka Connect to stream Twitter data into Adobe Experience Platform

## Prerequisites

- Java JDK11 or above needs to be installed on your computer, you can download that JDK here: [https://www.oracle.com/java/technologies/javase-jdk11-downloads.html](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- Access to Adobe Experience Platform

## Architecture Overview

Have a look at the below architecture, which highlights the components that will be discussed and used in this module.

![Architecture Overview](../assets/images/architecturem24.png)

## Sandbox to use

{% hint style="info" %}
Kindly refer to [Exercise 0.0](../getting-started/ex0.md) for instructions on how to find your Sandbox ID and other identifying values.
{% endhint %}

## Exercises

[15.1 Introduction to Apache Kafka](./ex1.md)

In this exercise, you'll learn about the basics of Apache Kafka

[15.2 Install and configure your Kafka cluster](./ex2.md)

In this exercise, you'll download, install and configure your basic Apache Kafka cluster.

[15.3 Configure HTTP API Streaming endpoint in Adobe Experience Platform](./ex3.md)

In this exercise, you'll configure an HTTP API Source Connector in Adobe Experience Platform.

[15.4 Install and configure Kafka Connect and the Adobe Experience Platform Sink Connector](./ex4.md)

In this exercise, you'll use Kafka Connect to install and use the Adobe Experience Platform Sink Connector and you'll send events into Adobe Experience Platform manually.

[Summary and benefits](./summary.md)

Summary of this module and overview of the benefits.

{% hint style="info" %}
Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact the Solution Partner Portal, by sending an email to **spphelp@adobe.com**.
{% endhint %}

