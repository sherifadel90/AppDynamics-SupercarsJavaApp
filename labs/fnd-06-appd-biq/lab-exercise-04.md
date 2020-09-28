# Configure HTTP Data Collectors

Data collectors allow you to supplement business transaction and transaction analytics data with application data. The application data can add context to business transaction performance issues. For example, they show the values of particular parameters or return value for business transactions affected by poor performance. 
This data shows the business context affected by performance issues, such as the specific user, order, or product.  

HTTP data collectors capture the URLs, parameter values, headers, and cookies of HTTP messages exchanged in a business transaction. 

In this exercise you will perform the following tasks:
- Enable all HTTP Data Collectors
- Observe and Select relevant HTTP Data Collectors
- Capture Business Data in Analytics using HTTP Params
- Validate Analytics on HTTP Parameters

## Enable all HTTP Data Collectors

Initially we can Capture all HTTP Data Collectors to find out what would be the useful parameters that we can capture into Analytics and use it in our Dashboards

1.	Select the Applications tab at the top left of the screen.
2.	Select SuperCars Application
3.	Select the Configuration Left tab.
4.	Click on the Instrumentation Link.
5.	Select the Data Collectors tab.
6.	Click on the Add Button in the HTTP Request Data Collectors

![HTTPDataCollectors 1](assets/images/06-http-data-collectors-03.png)


### Linux and Mac OS

1. In a new terminal window, run an `scp` command to upload the Java agent zip file to the `/tmp` directory of the Application VM.

  ```bash
  scp /tmp/db-agent-20.4.0.1730.zip centos@application.vm.ip.address:/tmp/
  ```

  In the example above, the Java agent zip file that you downloaded in the previous exercise is located in the `/tmp` directory of your local desktop. Be sure to edit the command to reflect your own environment.

  - The file name of your Java agent zip file may be slightly different than the one seen in the example.
  - The `application.vm.ip.address` needs to be replaced with actual IP address of the Application VM.


2. You will be prompted for the password for the Application VM. Enter the password to complete the command.

3. Open a new terminal window and use SSH to connect to your Application VM. Edit the command to reflect the actual IP Address of the Application VM.

  ```
  ssh centos@application.vm.ip.address
  ```

4. You will be prompted for the password for the Application VM. Enter the password to complete the command.

### Windows

You will need [WinSCP](https://winscp.net/download/WinSCP-5.17.2-Setup.exe) or another SCP client installed to upload the Java agent zip file to the Application VM. WinSCP also includes the SSH client [PuTTY](https://www.putty.org/).

Before you upload the agent file, you will need to add a new site in WinSCP for your Application VM.

1. Enter the IP Address for your Application VM.
2. Enter the Username for your Application VM.
3. Enter the Password for your Application VM.
4. Click the **Save** button.

![WinSCP 1](assets/images/04-winscp-01.png)

When you have added the site, you can log into the Application VM and upload the agent file.

1. In WinSCP, select the new site you created for your Application VM.
2. Click **Login**.

![WinSCP 2](assets/images/04-winscp-02.png)

1. Navigate to the `/tmp` directory and select **Binary** for Transfer Settings.

![WinSCP 3](assets/images/04-winscp-03.png)

1. Navigate to the directory where you downloaded the agent file.
2. Right-click on the file, and select **Copy**.

![WinSCP 4](assets/images/04-winscp-04.png)

1. Paste the agent zip file into the `/tmp` directory in the WinSCP window by right-clicking on the right pane within WinSCP and selecting **Paste**

![WinSCP 5](assets/images/04-winscp-05.png)

Open an SSH window to your Application VM.
1. Click the **New Session** tab.
2. Select the new site you created for your Application VM.
3. Click the arrow on the right side of the **Login** button and select **Open in PuTTY**

![WinSCP 6](assets/images/04-winscp-06.png)

## Unzip the file into a specific directory on the file system

1. Create the directory structure where you will unzip the Java agent zip file.

  ```
  cd /opt/appdynamics
  mkdir dbagent
  ```
  You should now be able to see the new directory structure to which the Database Visibility agent zip file will be copied.

  ![DB Install 1](assets/images/04-dbagent-install-01.png)

1. Copy the Database Visibility agent zip file to the directory and unzip the file. The name of your Database Visibility agent file may be slightly different than the example below.

  ```
  cp /tmp/db-agent-20.4.0.1730.zip /opt/appdynamics/dbagent/
  cd /opt/appdynamics/dbagent
  unzip db-agent-20.4.0.1730.zip
  ```
  The results of unzipping the file will be similar to the following image.

  ![DB Install 2](assets/images/04-dbagent-install-02.png)

## Start the Database Visibility agent

Start the Database Visibility agent and verify that it started with the following commands:

```
cd /opt/appdynamics/dbagent
nohup java -Dappdynamics.agent.maxMetrics=300000 -Ddbagent.name=DBMon-Lab-Agent -jar db-agent.jar &
ps -ef | grep db-agent
```

The results should be similar to the following image.

![DB Install 3](assets/images/04-dbagent-install-03.png)

You can read more about installing the AppDynamics Database Visibility agent [here](https://docs.appdynamics.com/display/latest/Overview+of+Database+Visibility) and [here](https://docs.appdynamics.com/display/latest/Install+the+Database+Agent)

**Next**: Configure a Database Collector in the Controller
