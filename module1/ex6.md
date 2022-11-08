---
title: Foundation - Setup of Adobe Experience Platform Data Collection and the Web SDK extension - Implement Adobe Target
description: Foundation - Setup of Adobe Experience Platform Data Collection and the Web SDK extension - Implement Adobe Target
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 4aee8ae2-38ca-49a3-8f1b-57713d16f5b5
---
# 1.6 Implement Adobe Target

## 1.6. Update your Datastream to use Adobe Target

In case you want to send data collected by Web SDK to Adobe Target and get a response from Adobe Target with a personalized experience for every customer, follow these steps.

Go to [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/) and go to **Datastreams**. 

In the top right corner of your screen, select your sandbox name, which should be `--aepSandboxId--`. Open your specific datastream, which is named `--demoProfileLdap-- - Demo System Datastream`.

![Click Edge Configuration icon in the left navigation](./images/edgeconfig1b.png)

You'll then see this. To enable Adobe Target, click **+Add Service**.

![AEP Debugger](./images/aa2.png)

You'll then see this. Select the service **Adobe Target**, after which you can optionally provide additional information. At this moment, there's no need to save this, so click **Cancel**.

![AEP Debugger](./images/at1.png)

Next Step: [1.7 XDM Schema requirements in Adobe Experience Platform](./ex7.md)

[Go Back to Module 1](./data-ingestion-launch-web-sdk.md)

[Go Back to All Modules](./../../overview.md)
