
# Dashboard Components 

The ability to build dashboards is a vital skill to demonstrate and utilize AppDynamics Capabilities and Value. 
In this exercise, We will be working through a few of the Useful Dashboard Components that can be used to build compelling dashboards.

## Create a new Dashbaord
1. Select the **Dashbaord & Reports** tab at the top left of the screen.
2. Click on **Create Dashboard** Button
3. In the Popup Window, Type the Dashbaord Name
4. In the Popup Window, select **Absolute** as the **Canvas Type**
5. Click **Ok**
![NewDashboard](assets/images/06-new-dashboard-01.png)

Now Open the newly created  empty  Dashboard and let's start adding various widget types.

## Dashboard Components: Custom Widget Builder
Benefits:
1.	Very Flexible
2.	Can generate, Numeric, Timeseries, Pie charts, etc.. 
3.	Based on AppDynamics "AD" Query Language 

Now, let's start Creating one
1. Toggle the **Edit Mode** at the upper left corner of the dashboard
2. Click on **Add Widget** Button
3. In the Popup Window, Select the **Analytics** Tab  on the left
4. Then Click on **Custom Widget Builder**
![NewCustomWidgetBuilder](assets/images/06-custom-widget-02.png)

Once opened,  you'll notice that there are various type of Chart  Types that we can create in the Customer Widget Builder, and either by Drag or Drop, or by AD Query in the Advance pane, thus showing the Benefits discussed ealier.
![NewCustomWidgetBuilder](assets/images/06-custom-widget-details-03.png)

For now, we will cover Bar and Pie Charts.

### Numeric Type
 **Exercise:** Quantifying the $ Amount Impacted due to Errors is significant to every Application Owner, Where we can show the Customer how much his  IT have Impacted the business revnue and tthus resulting in money/profit loss
1. Select "Numeric" from the Chart Types on the right
2. Add a filter on the "/Supercar-Trader/sell.do" Business Transactions
3. Add a filter on the "Error" User Experience to show what was impacted due to Errors
4. Add “CarPrice_MIDC" in the Y-Axis, notice that SUM is the Aggregation used to capture the total Price per Model
5. Change  the Font Color to Red to better present it.
5. Click on Save
![NumericChartWidget](assets/images/06-numeric-chart-widget-08.png)

Note that we could do the same for the $ Amount Transacted Succesfully by changingn the User Experience filter to only include NORMAL, SLOW and VERY SLOW.

Bonus Point: We could baseline this Metric by Creating a Custom Metric in the Analytics Module, and defining a Health Rule to represent if the $ Amount Impacted is as expected or even  higher than the  norm (versus the Baseline).
Also it  will always be nice to add a Label for the Currency.
![NumericChartSamples](assets/images/06-numeric-chart-widget-samples-09.png)


### Bar Charts Type
 **Exercise:** Visualizing Top Impacted Car Models, where we will have a Bar Chart, showing the Car Models of all of the SellCar Trasnactions, categorised by the User Experience
1.	Select "Bar" from the Chart Types on the right
2.	Add a filter on the "/Supercar-Trader/sell.do" Business Transactions
3.	Add “CarModel_MIDC" in the X-Axis
4.	Add “User Experience" in the X-Axis
5.	Click on Save
![BarChartWidget](assets/images/06-bar-chart-widget-04.png)

Bonus Point: This Chart Type Can be utilised based on your need, to group in the X-AXIS by Customer Type, Company, Organization or any other relevant grouping if exists, below  are  some inspirations
![BarChartSamples](assets/images/06-bar-chart-widget-samples-05.png)


### Pie Charts Type
**Exercise:** Visualizing $ Sold by Car Models, where we will have a Pie Chart, showing the Car Models of all of the SellCar Trasnactions, and the sum of Prices per Model to know the most  Demanded Car Model on the Application, now that is defiently a Business View
1.	Select "Pie" from the Chart Types on the right
2.	Add a filter on the "/Supercar-Trader/sell.do" Business Transactions
3.	Add “CarModel_MIDC" in the X-Axis
4.	Add “CarPrice_MIDC" in the Y-Axis, notice that SUM is the Aggregation used to capture the total Price per Model
5.	Click on Save
![PieChartWidget](assets/images/06-pie-chart-widget-06.png)

**Bonus Point:** This Chart Type Can be utilised based on your need, below  are  some inspirations
![PieChartSamples](assets/images/06-pie-chart-widget-samples-07.png)


## User Journeys

## Conversion Funnels
