# AtliQ Mart FMCG Supply Chain-Dashboard




## Problem Statement	
AtliQ Mart is currently facing a problem where a few key customers did not extend their annual contracts due to service issues. It is speculated that some of the essential products were either not delivered on time or not delivered in full over a continued period, which resulted in bad customer service. Management wants to fix this issue before expanding to other cities. Hence, the management wants to track the "On-Time" & In-Full" delivery service levels for all the customers on daily basis to fix them and later expand the business to new cities.
## Steps followed
•	Step 1: Imported the excel files into the PowerBI.

•	Step 2: In the power query editor analysed the data for data munging.

•	Step 3: In the data model checked for the relationship and established relationship between 2 tables manually by dragging and dropping. Dim_date(date) to fact_order_lines(actual_delivery_date).

•	Step 4: Created a table name key_measures. Under that created 2 dax expression, Delayed and Deliveries.

•	Step 5: The following DAX expression was written for Delayed.

    Delayed = count(fact_order_lines[actual_delivery_date]) - COUNT(fact_order_lines[agreed_delivery_date].[Day])

•	Step 6: The following DAX expression was written for Deliveries:

    Deliveries = 
    COUNTROWS(
        FILTER(
            'fact_order_lines',
            NOT(ISBLANK('fact_order_lines'[actual_delivery_date])) || NOT(ISBLANK(fact_order_lines[agreed_delivery_date]))
        ))

•	Step 7: Created 4 more measures which is IF%, OT%, OTIF% and Total Order Aggregate. They all were put into a single folder named order_aggregate.

•	Step 8: Dax expression was written for IF%:

    IF % = DIVIDE(SUM(fact_orders_aggregate[in_full]),[Total Order Agregate],0)

•	Step 9: Dax expression was written for OT%:

    OT % = DIVIDE(SUM(fact_orders_aggregate[on_time]),[Total Order Agregate],0)
•	Step 10: Dax expression was written for OTIF%:

    OTIF % = DIVIDE(sum(fact_orders_aggregate[otif]),[Total Order Agregate],0)
•	Step 11: Dax expression was written for Total Order Aggregate:

    Total Order Aggregate = COUNT(fact_orders_aggregate[order_id])
•	Step 12: Created 3 more measures which is LIFR%, VOFR% and Total Order Line. They all were put into a single folder named order_Line.

•	Step 13: Dax expression was written for LIFR%:

    LIFR % = DIVIDE(sum(fact_order_lines[In Full]),[Total Order Line],0)
•	Step 14: Dax expression was written for VOFR%:

    VOFR % = DIVIDE(SUM(fact_order_lines[delivery_qty]),sum(fact_order_lines[order_qty]))
•	Step 15: Dax expression was written for Total Order Line:

    Total Order Line = COUNT(fact_order_lines[order_id])
•	Step 16: Created 3 more measures which is Target_IF%, Target_OT % and Target_OTIF%. They all were put into a single folder named Order_Target.

•	Step 17: Dax expression was written for Target_IF%:

    Target_IF % = AVERAGE(dim_targets_orders[infull_target%])/100
•	Step 19: Dax expression was written for Target_OT%:

    Target_OT % = AVERAGE(dim_targets_orders[ontime_target%])/100
•	Step 20: Dax expression was written for Target_OTIF%:

    Target_OTIF % = AVERAGE(dim_targets_orders[otif_target%])/100
•	Step 21: Finally, DAX expression was written for Product QTY:

    Product QTY = SUM(fact_order_lines[order_qty]) 
•	Step 22: Dashboard process

•	Step 23: Three gauges were added to the canvas to show the target along with the current percentage. one representing IF%, second depicting OT% and lastly OTIF%.
## Snapshot of IF%
![Screenshot 2024-06-17 095126](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/a8f3d970-56fd-4a6a-a234-165c0d3d1e62)
## Snapshot of OT%
![Screenshot 2024-06-17 095245](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/4d49adb3-6192-4168-9c8d-753f9dee3cdc)
## Snapshot of OTIF%
![Screenshot 2024-06-17 095343](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/c6023748-f2a3-42d5-b7ec-173020e8f775)

•	Step 24: Three cards were added to the canvas one representing Total Order, second depicting Distinct product and lastly Distinct Customer.
## Snapshot of Total Order
![Screenshot 2024-06-17 095354](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/895c08e9-913c-4f1f-82ac-6a374fe55353)
## Snapshot of Distinct product
![Screenshot 2024-06-17 095412](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/2d039891-e29a-4e5a-90db-087b158996cc)
## Snapshot of Distinct Customer
![Screenshot 2024-06-17 095423](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/53b0478a-c16e-4e97-ba12-10e035abb418)

•	Step 25: Table was added to the design area to show the total percentage. While creating this visual, City, Customer Id, OT%, Target OT%, IF%, Target IF%, OTIF% and Target OTIF% were added to the columns.

•	Step 26: For this table in the cell element background colour was used to show low to high percentages. But only for the columns OT%, IF% and OTIF%.
## Snapshot of Table

![Screenshot 2024-06-17 095439](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/4bca88f7-daef-4e0e-97d8-045ec797861b)

•	Step 27: Finally, 3 Filters were added to the dashboard which will be filtered by month, city and customer.
## Snapshot of Filter by Month
![Screenshot 2024-06-17 095451](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/e81607f5-eec5-4c98-b862-1c1056a4f6b6)

## Snapshot of Filter by City
![Screenshot 2024-06-17 095506](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/c9406517-b639-4e2b-b092-529e2aa28825)

## Snapshot of Filter by Customer
![Screenshot 2024-06-17 095521](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/38614945-5637-4363-8f68-839a7bff0c3e)

## Report snapshot (Power BI DESKTOP)
![Screenshot 2024-06-17 095538](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/fd3a8785-7b7c-4c3f-8d44-68c43f7d1867)

•	Step 28: The second Dashboard was created to show the performance metrics. 

•	Step 29: Started with five buttons which is used to show OT%, IF%, OTIF%,LIFR% and VOFR%. Bookmarks were utilised to show area charts for each of the buttons.
## Snapshot of 5 buttons
![Screenshot 2024-06-17 095647](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/f1703828-94fd-419f-a3d4-bacdd52eaf65)

•	Step 30: Five area charts were used to represent percentage and target along with month. 

•	Step 31: For the first area chart mmm_yy(month) was added to the X Axis and OT%, Target_OT% added to the Y Axis.
## Snapshot of OT% Area Chart
![Screenshot 2024-06-17 095717](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/8c7d0d96-762e-4d94-bd41-0b7d461526c2)

•	Step 32: For the 2nd area chart mmm_yy(month) was added to the X Axis and IF%, Target_IF% added to the Y Axis.
## Snapshot of IF% Area Chart

![Screenshot 2024-06-17 095727](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/a250caf2-815a-4036-960b-05f9363e0468)

•	Step 33: For the 3rd area chart mmm_yy(month) was added to the X Axis and OTIF%, Target_OTIF% added to the Y Axis.
## Snapshot of OTIF% Area Chart
![Screenshot 2024-06-17 095742](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/d9da0c9a-09ff-49c8-be1e-536be3ddb950)

•	Step 34: For the 4th area chart mmm_yy(month) was added to the X Axis and LIFR% added to the Y Axis.
## Snapshot of LIFR% Area Chart
![Screenshot 2024-06-17 095821](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/4234301b-2f25-4860-94e8-488ed25be8f5)

•	Step 35: For the 5th area chart mmm_yy(month) was added to the X Axis and VOFR% added to the Y Axis.
## Snapshot of VOFR% Area Chart
![Screenshot 2024-06-17 095835](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/9cbf5155-58fe-46a1-8991-17d7d50d355e)
## Report Snapshot Performance Metrics(Power BI DESKTOP)
![Screenshot 2024-06-17 095903](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/c64419fd-f607-4c7c-92bf-087bac3f77d0)

•	Step 36: Created product insight dashboard

•	Step 37: One clustered bar chart was added to the canvas to illustrate sum of order quantity by category and city. Category was added to the X axis, sum of order Qty was added to the Y axis and city was added to the legend.
## Snapshot of sum of order quantity by category & city
![Screenshot 2024-06-17 095917](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/6958b52f-dd25-4a8d-8a97-1b9f02d39a39)

•	Step 38: One table was added to the design area to show the total percentage. While creating this visual product name, LIFR% and VOFR% were added to the columns.

•	Step 39: Moreover, for the LIFR% AND VOFR% sparkline was created where product name was added to the Y axis.
## Snapshot of Table
![Screenshot 2024-06-17 095930](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/da33b89a-6221-4311-b7fe-aa5fa5f671bf)

•	Step 40: Three cards were added to the dashboard to show Delayed, Deliveries and product QTY. The snapshot are as follows.

![Screenshot 2024-06-17 095940](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/6ca2df69-0a77-4e92-983b-a42e1a4affc3)
![Screenshot 2024-06-17 100002](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/94834304-db65-4226-859e-2eaf659830fe)
![Screenshot 2024-06-17 100012](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/9e51b32e-b2d7-4138-b535-0bc6913bf6cf)

•	Step 41: Finally three filters were also added to filter by city, month and customer.

![Screenshot 2024-06-17 100022](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/f46ec140-0b06-487b-9c57-056104bc83b5)
## Report Snapshot of Product Insight(Power BI DESKTOP)
![Screenshot 2024-06-17 100036](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/09e587da-67d2-47bf-9bcc-002f9cebdf04)

•	Step 42: Report Insight dashboard was created in the final to summarise with Top 5 customers, lowest and highest values in the month, most and least frequently ordered products and city with fewest orders.

•	Step 43: One table was used in the canvas to show the top 5 customers where customer name and sum of order quantity was added to the column. In the filters pane Top N was selected and to the by value sum of order quantity was added to get the result.

 # Snapshot of Top 5 Customers
![Screenshot 2024-06-17 100047](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/18198440-ec24-41e7-aa53-7481290940a7)

•	Step 44: Copy Pasted the VOFR% area chart to the report insight dashboard to highlight the lowest and highest records within the year. Slicer was also enabled which now makes it more convenient to zoom in and zoom out.
## Snapshot of VOFR%
![Screenshot 2024-06-17 100104](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/a120ac0d-b682-49d7-80dd-bc5dda2ebea3)

•	Step 45: Inserted arrow buttons to all the dashboard to navigate the pages.
## Snapshot of buttons
![Screenshot 2024-06-17 100158](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/51672c0a-6a3d-4db9-80c8-a1c8c090d64f)

![Screenshot 2024-06-17 100206](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/261c94e1-54e1-404a-89e8-529db48ca0ca)
## Snapshot of Report Insight( Power BI DESKTOP)
![Screenshot 2024-06-17 100129](https://github.com/AzeemArjunan/Sales-Insight-PBI/assets/171835611/3cb28e43-4c12-4b24-bdbc-81b8b4c2dc56)



