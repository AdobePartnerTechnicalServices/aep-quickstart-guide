---
title: Intelligent Services - Customer AI Create a New Instance (Configure)
description: Customer AI - Create a New Instance (Configure)
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: d9377c97-efed-427a-a063-aa9c6bd1a78a
---
# 5.2 Customer AI - Create a New Instance (Configure)

Customer AI works by analyzing existing Consumer Experience Event data to predict churn or conversion propensity scores. Creating a new Customer AI instance allows marketeers to define goals and measures.

## 5.2.1 Setup a new Customer AI instance

In Adobe Experience Platform, click **Services** in the left menu. The **Services** browser appears and displays all available services at your disposal. In the card for Customer AI, click **Open**.

![Service navigation](./images/navigatetoservice.png)

Click **Create instance**.

![Create new instance](./images/createnewinstance.png)

You'll then see this.

![Create new instance](./images/custai1.png)

Enter the required details for the Customer AI instance:

- Name: use `--demoProfileLdap-- Product Purchase Propensity`
- Description: use: **Predict the likelihood for customers to purchase a product**
- Propensity type: select **Conversion**

![Setup page 1](./images/setuppage1.png)

Click **Next**.

![Setup page 1](./images/next.png)

You'll then see this. Select the dataset you created in the previous exercise which is named `--demoProfileLdap - Demo System - Customer Experience Event Dataset`. Click **Next**.

![Setup page 1](./images/custai2.png)

Select **Will occur** and define the field **commerce.purchases.value** as the target variable.

![Defining CAI Goal](./images/caidefinegoal.png)

Click **Next**.

![Setup page 1](./images/next.png)

Next, set your schedule to run **Weekly** and set the time as close as possible to your current time. Ensure that the toggle **Enable scores for Profile** is enabled.

![Define CAI advance](./images/caiadvancepage.png)

Click **Finish**.

![Setup page 1](./images/finish.png)

You'll then see this popup. Click **OK**.

![Setup page 1](./images/finish1.png)

After you configure the instance, you can see it in the Customer AI instance list and also preview the summary of the setup and execution details by clicking on the Customer AI instance row. The summary panel will also display error details in case errors have been found.

![Instance setup summary](./images/caiinstancesummary.png)

{% hint style="info" %}
You can modify any definition or attribute as long as your Customer AI instance's status is either **Awaiting training** or **Error**
{% endhint %}
