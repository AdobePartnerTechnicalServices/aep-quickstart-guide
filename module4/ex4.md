---
title: Query Service - Power BI/Tableau
description: Query Service - Power BI/Tableau
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 11525d05-1c19-4d41-8f47-4feb3e8aed66
---
# 4.4 Generate a dataset from a query

## Objective

Learn how to generate datasets from query results
Connect Microsoft Power BI Desktop/Tableau directly to the Query Service
Creating a report in Microsoft Power BI Desktop/Tableau Desktop

## Lesson Context

A command line interface to query data is exciting but it doesn't present well. In this lesson, we will guide you through a recommended workflow for how you can use Microsoft Power BI Desktop/Tableau directly the Query Service to create visual reports for your stakeholders.

## 4.4.1 Create a dataset from a SQL query

The complexity of your query will impact how long it takes for the Query Service to return results. And when querying directly from the command line or other solutions like Microsoft Power BI/Tableau the Query Service is configured with a 5 minute timeout (600 seconds). And in certain cases these solutions will be configured with shorter timeouts. To run larger queries and front load the time it takes to return results we offer a feature to generate a dataset from the query results. This feature utilizes the standard SQL feature know as Create Table As Select (CTAS). It is available in the Platform UI from the Query List and also available to be run directly from the command line with PSQL.

In the previous you've replaced **enter your name** with your own ldap before executing it in PSQL.

```sql
select /* enter your name */
       e.--aepTenantId--.identification.core.ecid as ecid,
       e.placeContext.geo.city as city,
       e.placeContext.geo._schema.latitude latitude,
       e.placeContext.geo._schema.longitude longitude,
       e.placeContext.geo.countryCode as countrycode,
       c.--aepTenantId--.interactionDetails.core.callCenterAgent.callFeeling as callFeeling,
       c.--aepTenantId--.interactionDetails.core.callCenterAgent.callTopic as callTopic,
       c.--aepTenantId--.interactionDetails.core.callCenterAgent.callContractCancelled as contractCancelled,
       l.--aepTenantId--.loyaltyDetails.level as loyaltystatus,
       l.--aepTenantId--.loyaltyDetails.points as loyaltypoints,
       l.--aepTenantId--.identification.core.loyaltyId as crmid
from   demo_system_event_dataset_for_website_global_v1_1 e
      ,demo_system_event_dataset_for_call_center_global_v1_1 c
      ,demo_system_profile_dataset_for_loyalty_global_v1_1 l
where  e.--aepTenantId--.demoEnvironment.brandName IN ('Luma Telco', 'Citi Signal')
and    e.web.webPageDetails.name in ('Cancel Service', 'Call Start')
and    e.--aepTenantId--.identification.core.ecid = c.--aepTenantId--.identification.core.ecid
and    l.--aepTenantId--.identification.core.ecid = e.--aepTenantId--.identification.core.ecid;
```

Navigate to the Adobe Experience Platform UI - [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

You will search for your executed statement in the Adobe Experience Platform Query UI by entering your ldap in the search field:

Select **Queries**, go to **Log** and enter your ldap in the search field.

![search-query-for-ctas.png](./images/search-query-for-ctas.png)

Select your query and click **Output Dataset**.

![search-query-for-ctas.png](./images/search-query-for-ctasa.png)

Enter `--demoProfileLdap-- Callcenter Interaction Analysis` as name and description for the dataset and press the **Run Query** button

![create-ctas-dataset.png](./images/create-ctas-dataset.png)

As a result, you will see a new query with a status **Submitted**.

![ctas-query-submitted.png](./images/ctas-query-submitted.png)

Upon completion, you will see a new entry for **Dataset Created** (you might need to refresh the page).

![ctas-dataset-created.png](./images/ctas-dataset-created.png)

As soon as your dataset is created (which can take 5-10 minutes), you can continue the exercise.

Next Step - Option A: [4.5 Query Service and Power BI](./ex5.md)

Next Step - Option B: [4.6 Query Service and Tableau](./ex6.md)
