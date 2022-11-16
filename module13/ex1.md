---
title: Segment Activation to Microsoft Azure Event Hub - Setup Event Hub in Azure
description: Segment Activation to Microsoft Azure Event Hub - Setup Event Hub in Azure
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 9434ac83-5554-48bf-838c-7346d571efbf
---
# 13.1 Configure your Microsoft Azure EventHub environment

Azure Event Hubs is a highly scalable publish-subscribe service that can ingest millions of events per second and stream them into multiple applications. This lets you process and analyze the massive amounts of data produced by your connected devices and applications.

## 13.1.1 What is Azure Event Hubs?

Azure Event Hubs is a big data streaming platform and event ingestion service. It can receive and process millions of events per second. Data sent to an event hub can be transformed and stored by using any real-time analytics provider or batching/storage adapters.

Event Hubs represents the **front door** for an event pipeline, often called an event ingestor in solution architectures. An event ingestor is a component or service that sits between event publishers (like Adobe Experience Platform RTCDP) and event consumers to decouple the production of an event stream from the consumption of those events. Event Hubs provides a unified streaming platform with time retention buffer, decoupling event producers from event consumers.

## 13.1.2 Create a Event Hubs namespace

Go to [https://portal.azure.com/#home](https://portal.azure.com/#home) and select **Create a resource**. 

![1-01-open-azure-portal.png](./images/1-01-open-azure-portal.png)

In the resource screen, enter **Event** in the search bar and select **Event Hubs** from the dropdown:

![1-02-search-event-hubs.png](./images/1-02-search-event-hubs.png)

Click **Create**:

![1-03-event-hub-create.png](./images/1-03-event-hub-create.png)

If this is the first time that you create a resource in Azure, you will need to create a new **Resource group**. If you have already a resource group you can select it (or create a new one).

Select **Create new**, name your group `--demoProfileLdap---aep-enablement`.

![1-04-create-resource-group.png](./images/1-04-create-resource-group.png)

Complete the test of the fields as indicated:

- Namespace : Define your namespace, it has to be unique, use the following pattern `--demoProfileLdap---aep-enablement`
- Location: **West-Europe** refers to the Azure datacenter in Amsterdam
- Pricing tier: **Basic**
- Throughput Units: **1**

![1-05-create-namespace.png](./images/1-05-create-namespace.png)

Click **Review + create**.

![1-06-namespace-review-create.png](./images/1-06-namespace-review-create.png)

Click **Create**.

![1-07-namespace-create.png](./images/1-07-namespace-create.png)

The deployment of your resource group can take 1-2 minutes, when successful you will see the following screen:

![1-08-namespace-deploy.png](./images/1-08-namespace-deploy.png)

## 13.1.3 Setup your Event Hub in Azure

Go to [https://portal.azure.com/#home](https://portal.azure.com/#home) and select **All resources**. 

![1-09-all-resources.png](./images/1-09-all-resources.png)

From the resource list, select your `--demoProfileLdap---aep-enablement` namespace:
  
![1-10-list-resources.png](./images/1-10-list-resources.png)
  
In `--demoProfileLdap---aep-enablement` detail screen, select **Event Hubs**:
  
![1-11-eventhub-namespace.png](./images/1-11-eventhub-namespace.png)

Click **+ Event Hub**.

![1-12-add-event-hub.png](./images/1-12-add-event-hub.png)

Use `--demoProfileLdap---aep-enablement-event-hub` as the name and click **Create**.

![1-13-create-event-hub.png](./images/1-13-create-event-hub.png)
  
Click **Event Hubs** in your event hub namespace. You should now see your **Event Hub** listed. If that is the case you can move on to the next exercise.

![1-14-event-hub-list.png](./images/1-14-event-hub-list.png)

## 13.1.4 Setup your Azure Storage Account

To debug your Azure Event Hub function in later exercises, you'll need to provide an Azure Storage Account as part of your Visual Studio Code project setup. You'll now create that Azure Storage Account.

Go to [https://portal.azure.com/#home](https://portal.azure.com/#home) and select **Create a Resource**.

![1-15-event-hub-storage.png](./images/1-15-event-hub-storage.png)

Enter **storage** in the search and select **Storage Account** from the list.

![1-16-event-hub-search-storage.png](./images/1-16-event-hub-search-storage.png)

Select **Create**.

![1-17-event-hub-create-storage.png](./images/1-17-event-hub-create-storage.png)

Specify your **Resource Group** (created in the beginning of this exercise), use `--demoProfileLdap--aepstorage` as your Storage account name, and select **Locally-redundant storage (LRS)**, then click **Review + create**.

![1-18-event-hub-create-review-storage.png](./images/1-18-event-hub-create-review-storage.png)

Click **Create**.

![1-19-event-hub-submit-storage.png](./images/1-19-event-hub-submit-storage.png)

Your Storage Account creation will take a couple seconds:

![1-20-event-hub-deploy-storage.png](./images/1-20-event-hub-deploy-storage.png)

When finished your screen will display the **Go to resource** button. 

Click **Microsoft Azure**.

![1-21-event-hub-deploy-ready-storage.png](./images/1-21-event-hub-deploy-ready-storage.png)

Your Storage Account is now visible under **Recent Resources**.

![1-22-event-hub-deploy-resources-list.png](./images/1-22-event-hub-deploy-resources-list.png)
