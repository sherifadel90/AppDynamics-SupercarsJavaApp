# Configure HTTP data collectors

Data collectors enable you to supplement business transaction and transaction analytics data with application data. The application data can add context to business transaction performance issues. For example, they show the values of particular parameters or return value for business transactions affected by  performance issues, such as the specific user, order, or product.  

HTTP data collectors capture the URLs, parameter values, headers, and cookies of HTTP messages that are exchanged in a business transaction.

In this exercise you will perform the following tasks:
- Enable all HTTP data collectors.
- Observe and Select relevant HTTP data collectors.
- Capture Business Data in Analytics using HTTP Params.
- Validate Analytics on HTTP Parameters.

## Enable all HTTP data collectors

Initially, you can capture all HTTP data collectors to learn which useful parameters you can capture into Analytics and use it in your Dashboards

> *Note*: It is strongly recommended that you perform this step on a UAT environment, not production.

1. Select the **Applications** tab at the top left of the screen.
2. Select **Supercar-Trader** Application
3. Select the **Configuration** Left tab.
4. Click on the **Instrumentation** Link.
5. Select the **Data Collectors** tab.
6. Click on the **Add** Button in the **HTTP Request Data Collectors**

![HTTPDataCollectors 1](assets/images/06-http-data-collectors-03.png)

You will now configure an HTTP data collector to capture all HTTP Parameters. You will only enable it on Transaction Snapshots to avoid any overheads until you identify the precise parameters that you need for Transaction Analytics

1. For the **Name**, specify **All HTTP Param**.
2. Enable Transaction Snapshots.
3. Do not enable Transaction Analytics.
4. Click on **+ Add** in the HTTP Parameters section.
5. For the new Parameter, specify **All** as the Display Name, and specify an asterisk  `*`  in the HTTP Parameter name.
6. Click **Save** and enable `/Supercar-Trader/sell.do` Transaction

![HTTPDataCollectors 2](assets/images/06-add-all-http-data-collectors-04.png)

## Observe and select relevant HTTP data collectors

1. Apply load on the Application, specifically the **SellCar** transaction. Open one of its snapshots with Full Call Graph, and select the **Data Collectors Tab**.

  You can now see all HTTP Parameters. You will see a number of key metrics, such as Car Price, Color, Year, and more.

![HTTPDataCollectors 2](assets/images/06-view-all-http-data-collectors-05.png)

2. Note the exact Parameter names to add them again in the **HTTP Parameters** list and enable them in Transaction Analytics.

3. Once they are added, delete the **All HTTP Param** HTTP data collector.

## Capture business data in analytics with HTTP Params

You will now configure the HTTP data collector again, but this time you will capture only the useful HTTP Parameters and enable them in Transaction Analytics.

1. In the Name, specify **CarDetails**.
2. Enable Transaction Snapshots.
3. Enable Transaction Analytics.
4. Click **+ Add** in the HTTP Parameters section.
5. For the new Parameter,  specify **CarPrice_http** as the Display Name, and specify **carPrice** as the HTTP Parameter name.
6. Repeat for the rest of the Car Parameters as shown below.
7. Click **Save** and enable on `/Supercar-Trader/sell.do` Transaction

![SaveHttpDataCollectors](assets/images/06-save-http-data-collectors-06.png)

## Validate analytics on HTTP parameters

You will now validate whether the business data was captured by HTTP data collectors in AppDynamics Analytics.

1. Select the **Analytics** tab at the top left of the screen.
2. Select the **Searches** tab and create a new drag and drop search.
3. Verify that the **Business Parameters** appear as a field in the Custom HTTP Request Data.
4. Validate that the **CarPrice** field has data.

![ValidateHttpDataCollectors](assets/images/06-validate-http-data-collectors-07.png)


**Next**: Configure a method invocation Data Collector
