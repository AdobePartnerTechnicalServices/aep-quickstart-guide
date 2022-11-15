---
title: Query Service - Explore the dataset with Tableau
description: Query Service - Explore the dataset with Tableau
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 04209eb4-b054-4a2e-885e-61f601c3fc2c
---
# 4.6 Query Service and Tableau

Open Tableau.

![start-tableau.png](./images/start-tableau.png)

In **Connect To a Server** select **PostgreSQL**:

![tableau-connect-postgress.png](./images/tableau-connect-postgress.png)

Go to Adobe Experience Platform, to **Queries** and to **Credentials**.

![query-service-credentials.png](./images/query-service-credentials.png)

From the **Credentials** page in Adobe Experience Platform, copy the **Host** and paste it in the **Server** field, copy the **Database** and paste it in the **Database** field in Tableau, copy the **Port** and paste it in the field **Port**in Tableau, do the same for **Username** and **Password**. Next, click **Sign In**.

Sign In:

![tableau-connection-dialog.png](./images/tableau-connection-dialog.png)

Click search (1) and enter your **ldap** into the search field, identify you table from the result set and drag (3) it onto the location named **Drag tables here**. When finished, click on **Sheet 1** (3).

![tableau-drag-table.png](./images/tableau-drag-table.png)

To visualize our data on the map we need to convert longitude and latitude to dimensions. In **Measures** select **Latitude** (1) and open the field's dropdown and select **Convert to Dimension** (2). Do the same for the **Longitude** measure.

![tableau-convert-dimension.png](./images/tableau-convert-dimension.png)

Drag the **Longitude** measure to the **Columns** and the **Latitude** measure to **Rows**. Automatically the map of **Belgium** will appear with little dots representing the cities in out data set.

![tableau-drag-lon-lat.png](./images/tableau-drag-lon-lat.png)

Select **Measure Names** (1), open the dropdown and select **Add to Sheet** (2):

![tableau-select-measure-names.png](./images/tableau-select-measure-names.png)

You will now have a map, with dots of various sizes. The size indicates the number of call center interactions for that specific city. To vary the size of the dots, navigate to the right panel and open **Measure Values** (using the drop down icon). From the drop down list select **Edit Sizes**. Play around with different sizes.

![tableau-vary-size-dots.png](./images/tableau-vary-size-dots.png)

To further display the data per **Call Topic**, drag (1) the **Call Topic** dimension onto **Pages**. Navigate through the different **Call topics** using the **Call Topic** (2) on the right side of the screen:

![tableau-call-topic-navigation.png](./images/tableau-call-topic-navigation.png)

You've now finished this exercise.
