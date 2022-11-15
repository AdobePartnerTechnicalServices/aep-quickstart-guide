---
title: Query Service - Explore the dataset with Power BI
description: Query Service - Explore the dataset with Power BI
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 0f9e6719-056b-4858-8c86-04b3beaa950e
---
# 4.5 Query Service and Power BI

Open Microsoft Power BI Desktop.

![start-power-bi.png](./images/start-power-bi.png)

Click **Get Data**.

![power-bi-get-data.png](./images/power-bi-get-data.png)

Search for **postgres** (1), select **Postgres** (2) from the list and **Connect** (3).

![power-bi-connect-progress.png](./images/power-bi-connect-progress.png)

Go to Adobe Experience Platform, to **Queries** and to **Credentials**.

![query-service-credentials.png](./images/query-service-credentials.png)

From the **Credentials** page in Adobe Experience Platform, copy the **Host** and paste it in the **Server** field, and copy the **Database** and paste it in the **Database** field in PowerBI, then click OK (2).

{% hint style="warning" %}
Make sure to include port **:80** at the end of the Server value because the Query Service does not currently use the default PostgreSQL port of 5432.
{% endhint %}

![power-bi-connect-server.png](./images/power-bi-connect-server.png)

In the next dialog populate the User name and Password with your Username and Password found in the **Credentials** of Queries in Adobe Experience Platform.

![query-service-credentials.png](./images/query-service-credentials.png)

In the Navigator dialog, put your **LDAP** in the search field (1) to locate your CTAS datasets and check the box next to each (2). Then click Load (3).

![power-bi-load-churn-data.png](./images/power-bi-load-churn-data.png)

Make sure the **Report** tab (1) is selected.

![power-bi-report-tab.png](./images/power-bi-report-tab.png)

Select the map (1) and after it is added to the reporting canvas, enlarge the map (2).

![power-bi-select-map.png](./images/power-bi-select-map.png)

Next we need to define the measures and the dimensions, you do this by dragging fields from the **fields** section onto the corresponding placeholders (located under **visualizations**) as indicated below:

![power-bi-drag-lat-lon.png](./images/power-bi-drag-lat-lon.png)

As measure we will use a count of **customerId**. Drag the **crmid** field from the **fields** section into the **Size** placeholder:

![power-bi-drag-crmid.png](./images/power-bi-drag-crmid.png)

Finally, to do some **callTopic** analysis, let's drag the **callTopic** field on to the **Page level filters** placeholder (you might have to scroll in the **visualizations** section);

![power-bi-drag-calltopic.png](./images/power-bi-drag-calltopic.png)

Select/unselect **callTopics** to investigate:

![power-bi-report-select-calltopic.png](./images/power-bi-report-select-calltopic.png)

You've now finished this exercise.
