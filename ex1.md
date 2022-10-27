---
title: Getting Started - Use Demo System Next to setup your Launch property
description: Getting Started - Use Demo System Next to setup your Launch property
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 9c0eddf5-bfd7-4e7a-a8e2-ccd55ccd966d
---
# 0.1 Use Demo System Next to setup your Adobe Experience Platform Data Collection client property

Once you've got access to Demo System, proceed with the below steps.

Go to [https://dashboard.adobedemo.com/](https://dashboard.adobedemo.com/). Select your sandbox and click **Quick Setup**.

![DSN](./images/dsnh1.png)

You'll see this:

![DSN](./images/dsnhome.png)

Under **General** - **Environment**, select your Adobe Experience Platform instance and your sandbox, in this case:

- **Experience Platform International**
- **aepenablementfy22**
- Configuration: please select **Global v2.0**

![DSN](./images/dsn1.png)

Next, select the preset **Enablement User** and click **Start**.

![DSN](./images/dsn2.png)

In the popup, enter a name for your Data Collection property. Please use this naming convention: **Demo System (DD/MM/YYYY)**. FYI: your LDAP will be appended automatically, you do not need to add it yourself.

Click **Start**.

![DSN](./images/dsn3.png)

You'll then see this popup, which is showing you the progress while creating your website and mobile app projects and your data collection properties.

![DSN](./images/dsn4.png)

Once the quick setup process has completed, you'll have:

- 1 Web Retail project, which makes it possible to use a demo website with the Luma demo brand
- 1 Mobile Retail project, which makes it possible to use a demo mobile app with the Luma demo brand
- 1 CX App Retail project, which makes it possible to use a call center and clienteling app with the Luma demo brand
- 1 Data Collection property for web, which you'll use to collect data from the website
- 1 Data Collection property for mobile, which you'll use to collect data from the mobile app

![DSN](./images/dsn5.png)

Keep this screen open as you'll need it in the next steps.

Next Step: [0.2 Create your Datastream](./ex2.md)

[Go Back to Module 0](./getting-started.md)

[Go Back to Overview](./overview.md)
