
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

### Bar Charts Type
 **Exercise:** Visualizing Top Impacted Car Models, where we will have a Bar Chart, showing the Car Models of all of the SellCar Trasnactions, categorised by the User Experience
1.	Select "Bar" from the Chart Types on the right
2.	Add a filter on the "/Supercar-Trader/sell.do" Business Transactions
3.	Add by “CarModel_MIDC" in the X-Axis
4.	Add by “User Experience" in the X-Axis
5.	Click on Save
![BarChartWidget](assets/images/06-bar-chart-widget-04.png)

Bonus Point: This Chart Type Can be utilised based on your need, to group in the X-AXIS by Customer Type, Company, Organization or any other relevant grouping if exists, below  are  some inspirations
![BarChartSamples](assets/images/06-bar-chart-widget-samples-05.png)


### Pie Charts Type
**Exercise:** Visualizing Top Impacted Car Models, where we will have a Bar Chart, showing the Car Models of all of the SellCar Trasnactions, categorised by the User Experience
1.	Select "Bar" from the Chart Types on the right
2.	Add a filter on the "/Supercar-Trader/sell.do" Business Transactions
3.	Add by “CarModel_MIDC" in the X-Axis
4.	Add by “User Experience" in the X-Axis
5.	Click on Save
![BarChartWidget](assets/images/06-bar-chart-widget-04.png)

Bonus Point: This Chart Type Can be utilised based on your need, to group in the X-AXIS by Customer Type, Company, Organization or any other relevant grouping if exists, below  are  some inspirations
![BarChartSamples](assets/images/06-bar-chart-widget-samples-05.png)


## User Journeys

## Conversion Funnels
