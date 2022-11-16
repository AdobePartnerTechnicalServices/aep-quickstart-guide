---
title: Install and configure your Kafka cluster
description: Install and configure your Kafka cluster
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: adffeead-9bcb-4632-9a2c-c6da1c40b7f2
---
# 15.2 Install and configure your Kafka cluster

## 15.2.1 Download Apache Kafka

Go to [https://kafka.apache.org/downloads](https://kafka.apache.org/downloads) and download the latest released version. Select the latest binary release, in this case **Scala 2.13**.

![Kafka](./images/kafka1.png)

You're then taken to a mirror site. Click the suggested link to download Kafka.

![Kafka](./images/kafka2.png)

Create a folder on your desktop named **Kafka_AEP** and place the downloaded file in that directory.

![Kafka](./images/kafka3.png)

Open a **Terminal** window by right-clicking your folder and clicking **New Terminal at Folder**.

![Kafka](./images/kafka4.png)

Run this command in your Terminal window to uncompress the downloaded file:

`tar -xvf kafka_2.13-3.1.0.tgz`

{% hint style="info" %}
Please verify that the above command matches the version of the file you downloaded. If your version is more recent, you'll need to update the above command to match that version.
{% endhint %}

![Kafka](./images/kafka5.png)

You'll then see this:

![Kafka](./images/kafka6.png)

After uncompressing that file, you now have a directory like this one:

![Kafka](./images/kafka7.png)

And in that directory, you'll see these subdirectries:

![Kafka](./images/kafka8.png)

Go back to your Terminal window. Enter the following command:

`cd kafka_2.13-3.1.0`

{% hint style="info" %}
Please verify that the above command matches the version of the file you downloaded. If your version is more recent, you'll need to update the above command to match that version.
{% endhint %}

![Kafka](./images/kafka9.png)

Next, enter the command `bin/kafka-topics.sh`. 

![Kafka](./images/kafka10a.png)

You should then see this response. This means that Kafka is properly installed and that Java is working fine. (Reminder: you need Java 8 JDK or Java 11 JDK installed for this to work!. You can see which Java version you have installed by using the command `java -version`.)

![Kafka](./images/kafka10.png)

## 15.2.2 Start Kafka

In order to start Kafka, you'll need to start Kafka Zookeeper and Kafka, in this order.

Open a **Terminal** window by right-clicking your folder **kafka_2.13-3.1.0** and clicking **New Terminal at Folder**.

![Kafka](./images/kafka11.png)

Enter this command:

`bin/zookeeper-server-start.sh config/zookeeper.properties`

![Kafka](./images/kafka12.png)

You'll then see this:

![Kafka](./images/kafka13.png)

Keep this window open while your going through these exercises!

Open another, new **Terminal** window by right-clicking your folder **kafka_2.13-3.1.0** and clicking **New Terminal at Folder**.

![Kafka](./images/kafka11.png)

Enter this command:

`bin/kafka-server-start.sh config/server.properties`

![Kafka](./images/kafka14.png)

You'll then see this:

![Kafka](./images/kafka15.png)

Keep this window open while your going through these exercises!

## 15.2.3 Create a Kafka topic

Open a **Terminal** window by right-clicking your folder **kafka_2.13-3.1.0** and clicking **New Terminal at Folder**.

![Kafka](./images/kafka11.png)

Enter this command to create a new Kafka topic with the name **aeptest**. This topic will be used for testing in this exercise.

`bin/kafka-topics.sh --create --topic aeptest --bootstrap-server localhost:9092`

![Kafka](./images/kafka16a.png)

You'll then see a similar confirmation:

![Kafka](./images/kafka17a.png)

Enter this command to create a new Kafka topic with the name **aep**. This topic will be used by the Adobe Experience Platform Sink Connector that you'll configure in the next exercises.

`bin/kafka-topics.sh --create --topic aep --bootstrap-server localhost:9092`

![Kafka](./images/kafka16.png)

You'll then see a similar confirmation:

![Kafka](./images/kafka17.png)

## 15.2.4 Produce events

Go back to the Terminal window in which you created your first Kafka topic and enter the following command:

`bin/kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic aeptest`

![Kafka](./images/kafka18.png)

You'll then see this. Every new line followed by pushing the Enter button will result in a new message being sent into the topic **aeptest**.

![Kafka](./images/kafka19.png)

Enter `Hello AEP` and push Enter. Your first event has now been sent into your local Kafka instance, into the topic **aeptest**.

![Kafka](./images/kafka20.png)

Enter `Hello AEP again.` and push Enter.

Enter `AEP Data Collection is the best.` and push Enter.

You've now produced 3 events into the topic **aeptest**. These events can now be consumed by an application that might need that data.

![Kafka](./images/kafka21.png)

On your keyboard, click `Control` and `C` at the same time to close your producer.

![Kafka](./images/kafka22.png)

## 15.2.4 Consume events

In the same Terminal window that you used to produce events, enter the following command:

`bin/kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic aeptest --from-beginning`

You'll then see all messages that were produced in the previous exercise for the topic **aeptest**, appear in the consumer. This is how Apache Kafka works: a producer creates events into a pipeline, and a consumer consumes those events.

![Kafka](./images/kafka23.png)

On your keyboard, click `Control` and `C` at the same time to close your producer.

![Kafka](./images/kafka24.png)

In this exercise, you've gone through all the basics to set up a local Kafka cluster, create a Kafka topic, produce events and consume events.

The goal of this module is to simulate what would happen if a real organization has already implemented an Apache Kafka cluster, and wants to stream data from their Kafka cluster into Adobe Experience Platform.

To facilitate such an implementation, an Adobe Experience Platform Sink Connector was created which can be implemented using Kafka Connect. You can find the documenation of that Adobe Experience Platform Sink Connector here: [https://github.com/adobe/experience-platform-streaming-connect](https://github.com/adobe/experience-platform-streaming-connect).

In the next exercises, you'll implement everything you need to use that Adobe Experience Platform Sink Connector from within your own local Kafka cluster.

Close your terminal window.

You have finished this exercise.
