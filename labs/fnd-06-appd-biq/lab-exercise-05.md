# Configure method invocation data collectors

Method invocation data collectors capture code data such as method arguments, variables, and return values. If HTTP data collectors don’t have sufficient business data, you can still capture these information from the code execution.

In this exercise you will perform the following tasks:
- Discover methods.
- Open a discovery session.
- Discover method parameters.
- Drill down to an object within the code.
- Create a method invocation data collector.
- Validate analytics on method invocation data collectors.

## Discover methods

In a typical business context, while monitoring your application, you might need to discover business data while selling a car, such as car price or model. First, you need to identify the method within the Application Code that will most likely contain this data.

1. Open one of the **"/Supercar-Trader/sell.do" Transaction Snapshots** with a full Call Graph.
2. **Drill into the Web-Portal** and expand the Call Graph.
3. You’ll notice a `saveCar` method** being called. This method is responsible for taking the user input and saving it to the database.

  ![DiscoverCallGraphMethods 1](assets/images/06-discover-callgraph-methods-01.png)

4. Right click on the method, and select `View Details`.
5. Note the **Full Class Name** and the **Method Name**.
  ```
  Class Name: supercars.dataloader.CarDataLoader
  Method Name: saveCar
  ```
  ![DiscoverCallGraphMethods 2](assets/images/06-discover-callgraph-methods-02.png)

## Open a discovery session

After identifying the method that is responsible for the Save Car operation, you will now identify the parameters that hold the business data.

You may not have an application developer available to identify this from the source code. However, there is an approach to discover the application methods and objects directly from AppDynamics.

1. Select the **Applications** tab at the top left of the screen.
2. Select **Supercar-Trader** application
3. Select the **Configuration** tab.
4. Click on the **Instrumentation** link.
5. Select the **Transaction Detection** tab.
6. Click on the **Live Preview Button** on the tight.
 ![OpenDiscoverySession](assets/images/06-open-discovery-session-03.png)

## Discover method parameters

1. Click on **Start Discovery Session Tab** at the top right of the screen
2. Select the **Web-Portal Node** in the pop-up windows. It should be the same node that the method you are investigating runs on

  ![OpenDiscoverySession](assets/images/06-start-discovery-session-04.png)

3. Select **Tools** on the right toggle.
4. Select **Classes/Methods** in the drop-down list.
5. Select **Classes** with name in the **Search** section.
6. Type in the class name `supercars.dataloader.CarDataLoader` in the text box.
7. Click **Apply** to search for the matching class methods.
8. Once the results appear, expand the class that matches your search.
9. Look for the same method that you noted earlier, `saveCar`.

  ![OpenDiscoverySession](assets/images/06-method-drill-down-05.png)

Note that the `saveCar` method takes a `CarForm` object as an input parameter.

## Drill Down to the Object

Now you have found the method, explore its parameters to find out where you can pull the car details properties.

You saw that `saveCar` method takes the complex object `CarForm` as an input parameter. This object will hold the form data that was entered on the application webpage. Next, you need to inspect that object and find out how you can pull the car details from it.

1. Type in the class name of the input object `supercars.form.CarForm` in the text box
2. Click **Apply** to search for the class methods.
3. When the results appear, expand the `supercars.form.CarForm` class that matches the search.
4. Look for the methods that will return the car details that you want. You will find `get` methods for price, model, color, and more.

 ![ObjectDrillDown](assets/images/06-object-drill-down-06.png)

## Create method invocation data collector

With the findings from the previous exercises, you can now configure a method invocation data collector to pull the car details directly from the running code in runtime.

1. Select the **Applications** tab.
2. Select **Supercar-Trader** Application
3. Select the **Configuration** tab.
4. Click on the **Instrumentation** link.
5. Select the **Data Collectors** tab.
6. Click **Add** in the **Method Invocation Data Collectors**.

  ![MIDCDataCollector](assets/images/06-midc-data-collectors-07.png)

We will create a method invocation data collector to capture the car details.

1. For the **Name**, specify `SellCarMI`.
2. Enable **Transaction Snapshots**.
3. Enable **Transaction Analytics**.
4. Select **with a Class Name that**.
5. Add `supercars.dataloader.CarDataLoader` as the **Class Name**.
6. Add `saveCar` as the **Method Name**.

 ![NewMIDCDataCollector](assets/images/06-new-midc-data-collectors-08.png)

Then as observed, the Input Parameter of Index 0 in SaveCar method was an on Object of Class `CarForm`, and then there is a Getter method inside that object that returns the car details properties such as `getPrice()`.

So to explain that how we fetched that value in the MIDC, we will do the below:

1. Click on `Add` to specify the new data that you want to collect.
2. In the **Display Name**, specify `CarPrice_MIDC`.
3. In the Collect Data From, select **Method Parameter of Index 0**, which is our **CarForm Object**.
4. For the **Operation on Parameter**, select **Use Getter Chain**. You will be calling a method inside CarForm to return the car details.
5. Then specify **getPrice()**, the Getter method inside the `CarForm` class that will return the price.
6. Click **Save**.
  ![CreateMIDCDataCollector1](assets/images/06-midc-data-collection-09.png)
7. Repeat the above steps for all the properties, including color, model, and any others that you want to collect data for.
  ![CreateMIDCDataCollector2](assets/images/06-midc-all-data-collection-10.png)
8. **Save MIDC**, and apply to the `"/Supercar-Trader/sell.do"` business transaction.


## Validate analytics on MD parameters

Go to the Website, and apply some manual load on the Sell Car Page by submitting the form couple of times.

You will now validate if the business data was captured by HTTP data collectors in AppDynamics Analytics.

1. Select the **Analytics** tab.
2. Select the **Searches** tab and create a new drag and drop search.
3. Verify that the **Business Parameters** appear as a field in the **Custom Method Data**.
4. Verify that the **CarPrice Field** has data.

![ValidateMIDCDataCollector](assets/images/06-validate-MIDC-11.png)

## Conclusion

You have now captured the business data from the Sell Car transaction from the node at runtime. This data can be used in the Analytical and Dashboard features within AppDynamics to provide more context to the business and measure IT impact on the business.

**Next**: Understand dashboard components
