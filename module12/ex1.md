---
title: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector - Create your Google Cloud Platform Account
description: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector - Create your Google Cloud Platform Account
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 632ff2fe-ae56-4481-b281-c11224b18639
---
# 12.1 Create your Google Cloud Platform Account

## Objectives

- Create your Google Cloud Platform Account
- Become familiar with Google Cloud Platform Console
- Create and prepare your BigQuery project

## 12.1.1 Why connect Google BigQuery to Adobe Experience Platform to get Google Analytics data

Google Cloud Platform (GCP) is a suite of public cloud computing services offered by Google. The Google Cloud Platform includes a range of hosted services for compute, storage and application development that run on Google hardware. 

BigQuery is one of these services and it is always included with Google Analytics 360. Google Analytics data is frequently sampled when we try to get data directly from it (API for example). That's why Google includes BigQuery to get unsampled data, so brands can do advanced analysis using SQL and benefit from the power of GCP.

Google Analytics data is loaded daily into BigQuery using a batch-mechanism. As such, it doesn't make any sense to use this GCP/BigQuery integration for Real-time personalization and activation use-cases.

If a brand wants to deliver real-time personalization use-cases based on Google Analytics data, it can collect that data on the website with Google Tag Manager and then stream it to Adobe Experience Platform in real-time. 

The GCP/BigQuery Source Connector should be used to...

- track all customer behavior on the website and load that data in Adobe Experience Platform for analysis, data science and personalization use-cases that don't require real-time activation.
- load Google Analytics historical data into Adobe Experience Platform, again for analysis and data science use-cases

## 12.1.2 Create your Google Account

In order to get a Google Cloud Platform account you need a Google account.

## 12.1.3 Activate your Google Cloud Platform Account

Now that you have you Google Account, you can create a Google Cloud Platform environment. To do that, go to [https://console.cloud.google.com/](https://console.cloud.google.com/).

On the next page, Accept the Terms & Conditions.

![demo](./images/ex1/1.png) 

Next, click on **Select a project**.

![demo](./images/ex1/2.png)

Click on **NEW PROJECT**.

![demo](./images/ex1/createproject.png)

Name your project following this naming convention:

| Convention         | Example|    
| ----------------- |-------------| 
| `--demoProfileLdap---googlecloud` | delaigle-googlecloud          |   

![demo](./images/ex1/3.png)

Click **Create**.

![demo](./images/ex1/3-1.png)

Wait until the notification in the top right side of your screen tells you that the creation is finished. Then, click  on **View project**.

![demo](./images/ex1/4.png)

Next, go to the search bar on top of the screen and type **BigQuery**. Select the first result.

![demo](./images/ex1/7.png)

You'll then be redirected to the BigQuery Console and you'll see a popup message. 

**Click Done**.

![demo](./images/ex1/5.png)

The goal of this module is to get Google Analytics data into Adobe Experience Platform. To do that, we need dummy data in a Google Analytics dataset to start with. 

Click on **Add Data** on the left side menu, followed by clicking **Explore public datasets**.

![demo](./images/ex1/18.png)

You'll then see this window: 

![demo](./images/ex1/19.png)

Enter the search term **Google Analytics Sample** in the search bar and select the first result.

![demo](./images/ex1/20.png)

You'll see the following screen with a description of the dataset. Click on **VIEW DATASET**.

![demo](./images/ex1/21.png)

You'll then be redirected to BigQuery where you'll see this **bigquery-public-data** dataset under **Explorer**.

![demo](./images/ex1/22a.png)

In **Explorer**, you should now see a number of tables. Feel free to explore them. Go to `google_analytics_sample`.

![demo](./images/ex1/22.png)

Click to open the table `ga_sessions`.

![demo](./images/ex1/23.png)

Before you continue with the next exercise, please write down the following things in a separate text file on your computer:

| Credential         | Naming| Example|   
| ----------------- |-------------| -------------|
| Project Name | `--demoProfileLdap---googlecloud` | vangeluw-googlecloud  |
| Project ID | random | composed-task-306413 |

You can find your Project Name and Project ID by clicking on your **Project Name** in the top menu bar:

![demo](./images/ex1/projectMenu.png)

You'll then see your Project ID on the right side:

![demo](./images/ex1/projetcselection.png)

You can now move to Exercise 12.2 where you'll get your hands dirty by querying Google Analytics data.
