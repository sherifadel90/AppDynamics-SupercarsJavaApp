# Enable Analytics on the Application

In this exercise you will access your AppDynamics Controller from your web browser and enable the Analytics from there.

In the example URL below, substitute the IP Address or fully qualified domain name of your Controller VM.

Example Controller URL for browser:

```
http://IP_OR_FQDN_OF_HOST:8090/controller
```

Access the controller login screen from your web browser. You should see the login page of the Controller like the image below.

![Controller Login Screen](assets/images/03-controller-login.png)

Use the following case-sensitive credentials to login:

- Username: `admin`
- Password: `welcome1`

Navigate to the Analytics Configuration

1. Select the **Home** tab at the top left of the screen.
2. Select the **Getting Started** tab.
3. Click **Getting Started Wizard**.
1.	Select the **Analytics** tab at the top left of the screen.
2.	Select the **Configuration** Left tab.
3.	Select the **Transaction Analytics - Configuration** tab.
4.	**Mark the Checkbox** next to the SuperCars Application


  ![Download Wizard 1](assets/images/03-download-wizard-01.png)

Select the agent for download.
1. Click **Databases**.

  ![Download Wizard 2](assets/images/03-download-wizard-02.png)

Download the Database Agent.

1. Select **MySQL** from the **Select Database Type** dropdown menu.
2. Accept the defaults for the Controller connection.
3. Click **Click Here to Download**.

  ![Download Wizard 3](assets/images/03-download-wizard-03.png)

Save the Database Visibility Agent file to your local file system.

Your browser should prompt you to save the agent file to your local file system, similar to the following image(depending on your OS).

![Download Wizard 4](assets/images/03-download-wizard-04.png)

**Next**: Install the Database Visibility Agent
