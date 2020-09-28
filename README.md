# Supercar Trader Readme

This is a simple Struts application which provides for an online supercar store which has some performance/code issues. The application can be built with Maven.

![image](doc-images/supercars-home.png)

## Architecture

The application is based on a Struts front end deployed on Apache Tomcat, using a [MySQL](https://www.mysql.com) back end.  MySql 5.7 is recommended.


## Database

The app uses a MySQL DB in the backend, the default schema is expected to be the "supercars" schema, and MySQL running on the same host as the application. The database build scripts are in "src/main/resources/db"

There are three scripts you will need to run in order:

- mysql-01.sql
- mysql-02.sql
- mysql-03.sql

The datasouce is defined in context.xml in src/webapp/META-INF

## Setup

### Application Server Setup

1. Have [Git](https://git-scm.com) installed and working
	<pre><code>
	sudo yum install git
 	</code></pre>
1. Use Git to obtain the WAR File code
	<pre><code>
	cd /opt/appdynamics
 	git clone https://github.com/Appdynamics/DevNet-Labs.git
 	</code></pre>
1. Install Java
	- Run the below (may change  based on your linux distribution)
		<pre><code>
 		sudo yum install java-1.8.0 (may vary based on your linux distro)
 		</code></pre>
	- Check the Java Version
		<pre><code>
 		java -version
		===OUTPUT===
		openjdk version "1.8.0_265"
		OpenJDK Runtime Environment (build 1.8.0_265-b01)
		OpenJDK 64-Bit Server VM (build 25.265-b01, mixed mode)
 		</code></pre>
1. Install Tomcat
	- We can download Apache tomcat 9 tar.gz either from its official Web site or using wget command from the terminal.
	- Install wget  command to  directly downlaod Tomcat on  our host fromt the internet
		<pre><code>
 		sudo yum install wget (may vary based on your linux distro)
 		</code></pre>
	- Install Tomcat
		<pre><code>
 		sudo wget http://www-eu.apache.org/dist/tomcat/tomcat-7/v7.0.106/bin/apache-tomcat-7.0.106.tar.gz
 		</code></pre>
	- Run the beneath tar command to extract Apache tomcat 7 under the /opt folder
		<pre><code>
 		sudo tar -zxpvf apache-tomcat-7.0.106.tar.gz  -C /usr/local/apache
		cd /usr/local/apache
		sudo mv apache-tomcat-7.0.106 apache-tomcat-7
		sudo chown -R [your-user]:[your-user] /usr/local/apache  (if you are not executing  as the root user)
 		</code></pre>
	- Before starting the Tomcat Service let’’s first set the required CATALINA_HOME environment variable using below commands :
		<pre><code>
		echo "export CATALINA_HOME='/usr/local/apache/apache-tomcat-7/'" >> ~/.bashrc
		source ~/.bashrc
		</code></pre>
1. Run Tomcat
	- By default no user or account is allowed to access Manager GUI Page and Admin Page. So to grant access to the users add the following lines in the file “/usr/local/apache/apache-tomcat-7/conf/tomcat-users.xml” at the end just above </tomcat-users> tag
		<pre><code>
		vi /usr/local/apache/apache-tomcat-7/conf/tomcat-users.xml
		</code></pre>
		Then add the below just above </tomcat-users> tag to create a User Admin Who can access manager and admin section both
		<pre><code>
		&lt;!-- User linuxtechi who can access only manager section --&gt; 
		&lt;role rolename="manager-gui" /&gt; 
		&lt;user username="manager" password="password" roles="manager-gui" /&gt; 
		&lt;!-- User Admin Who can access manager and admin section both --&gt; 
		&lt;role rolename="admin-gui" />
		&lt;user username="admin" password="password" roles="admin-gui" /&gt; 
		</code></pre>
	- By default, Tomcat manager is configured to be accessed from the same server where it’s installed. If you access manager, you will get 403 error, so For a manager to be accessible from any host/IP, you need to do the following:
		<pre><code>
		vi /usr/local/apache/apache-tomcat-7/webapps/manager/META-INF/context.xml
		</code></pre>
		Then comment the Valve Tag to be  similar  to  the below
		<pre><code>
		&lt;Context antiResourceLocking="false" privileged="true" &gt;
		&lt;!--
		  &lt;Valve className="org.apache.catalina.valves.RemoteAddrValve"
			 allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /&gt;
		-->
		  &lt;Manager sessionAttributeValueClassNameFilter="java\.lang\.(?:Boolean|Integer|Long|Number|String)|org\.apache\.catalina\.filters\.CsrfPreventionFilter\$LruCache(?:\$1)?|java\.util\.(?:Linked)?HashMap"/&gt;
		&lt;/Context&gt;
		</code></pre>
	- Start Tomcat
		<pre><code>
		cd /usr/local/apache/apache-tomcat-7/bin/
		./startup.sh
		</code></pre>
	- Open Tomcat URL in the browser to verify its isntallation
		<pre><code>
		Go to http://{ip-address-or-Hostname}:8080/
		</code></pre>

### Database Setup

### Application Deployment
1. Use the Tomcat Manager to deploy the war file
   - Go to Tomcat GUI at http://{ip-address-or-Hostname}:8080/
   - Click  on Manager App button on the right where  you'll be prompted to enter the Manager Credentails that we added in the “/usr/local/apache/apache-tomcat-7/conf/tomcat-users.xml” file  
   ![image](doc-images/Tomcat-Homepage.png)
   - To Deploy an Applicationn, You can either upload the WAR file through the Tomcat Manager web page or specify the path of the WAR file if it exists on Tomcat host
   - Since we've built our WAR file and it already  exists on the Server, we will use the second approach: 
   	- Scroll
		 - Scroll Down to the "Deploy directory or WAR file located on server" Section
		 - Contect Path: Defines the URL that end users will access the application from. So we will add "/Supercar-Trader" where our application can be accessed from a URL like http://{ip-address-or-Hostname}:8080/Supercar-Trader
		 - WAR or Directory Path: THe path of WAR file we generated from the Maven Build, which should be located at "/opt/appdynamics/DevNet-Labs/applications/Supercar-Trader/Supercar-Trader.war"
	-  Click  Deploy
	 ![image](doc-images/Tomcat-WAR-Deployment.png)
	
1. Now the app is available on "http://{ip-address-or-Hostname}:8080/Supercar-Trader" on your Tomcat instance

### Database Deployment
	
