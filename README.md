Getting-started-with-Cloud-Integration-service
==============================================

Getting started with Cloud Integration service

Tomado de https://www.ng.bluemix.net/docs/#services/CloudIntegration/index.html#gettingstartedwithcloudintegation

IBM® Cloud Integration for Bluemix™ service enables you to integrate cloud services with enterprise systems of record. This service exposes the backend systems of record as ReST APIs to be used by applications.

You can create an instance of the Cloud Integration service through Bluemix. This service can be used to interact with the backend system of record through APIs.
Connecting an Add-On
If you are logging on to Bluemix for the first time, before you proceed with creating a Cloud Integration service, you must connect to an add-on service.

    From the IBM Bluemix dashboard, click the Connect an Add-On link. The Add-Ons tiles are displayed on the Add-Ons page.
    Click the Cloud Integration add-on tile. The Cloud Integration Pick a Plan page displays the Plan, Features, and the Price for the add-on service.
    Select the App and Selected Plan and click Create.

You have successfully connected to the Cloud Integration add-on.
Before you begin

Before you begin exploring the Cloud Integration add-on service, you must ensure that you have the required secure connections and that you have created integrations. Once these two are in place, you can start creating Cloud Integration Enterprise APIs, Cast Iron Live Orchestration APIs, or Bluemix Apps APIs.
Managing the Enterprise Secure Connector

The Enterprise (DataPower) Secure Connector leverages and on-premise DataPower deployment as a secure gateway connection between backend resources (behind the enterprise firewall) and Bluemix applications ensuring high-availability/fail over and load balancing requirements. Follow the procedure given below to add and configure an enterprise Secure Connector.

    On the Manage Secure Connections page, specify the name of your connection in the Name your connection field.
    Click the Add and Configure button. Your enterprise secure connection name is displayed in the list of connectors.
    Configure the enterprise secure connector by completing the following:
        DataPower hostname or IP address
        Port number
        Browse for the DataPower server certificate
        Download the Cloud Integration service certificate
    Click Done to return to the Cloud Integration home page.

    Once the connection is established, you can successfully get started with creating APIs using the newly create DataPower connector.

Creating the Enterprise Secure Connector keys and certificates

    Log on to IBM WebSphere DataPower.
    Go to Network > Management > XML Management Interface.
    On the Configure XML Management Interface page, specify the following:
        Administrative state - Select the enabled option.
        Local address
        Port number
        Access control list
        Comments
        Enabled services
    Click Apply.
    Go to Administration > Miscellaneous > Crypto Tools. The Generate Key page is displayed.
    On the Generate Key page, specify the following:
        LDAP (reverse) Order of RDNs
        Country Name (C)
        State or Province (ST)
        Locality (L)
        Organization (O)
        Organizational Unit (OU)
        Organizational Unit 2 (OU)
        Organizational Unit 3 (OU)
        Organizational Unit 4 (OU)
        Common Name (CN)
        RSA Key Length
        File Name
        Validity Period
        Password
        Password Alias
        Export Private Key
        Generate Self-Signed Certificate
        Generate Key and Certificate Objects
        Object Name
        Using Existing Key Objects
    Click Generate. The confirmation page is displayed which lists the following keys and certificates that are generated:
        Private Key
        Certificate Signing Request
        Self-Signed Certificate
        Crypto Key object and Crypto Certificate object

Exporting self-signed certificates

    Log on to IBM WebSphere DataPower.
    Go to Administration > Main > File Management.
    Browse for the self-signed certificate file.
    In the Actions column, right-click Edit.
    Click Save Link As... option. Save the file to your local folder.

Creating a Cloud Gateway Service

    On the IBM WebSphere Data Power page, go to Services > Other Services > Cloud Gateway Service
    Click the Add button.
    Specify the required field details.
    In the Cloud Gateway inbound connections section, click the '+' symbol next to the SSL proxy profile. The SSL Proxy Profile page is displayed.
    Specify the relevant details to configure the SSL proxy profile. In the SSL Direction field, select the Reverse option.
    Click the '+' symbol next to the Reverse (Server) Crypto Profile. The Crypto Profile page is displayed.
    On the Crypto Profile page, specify the relevant details, especially the mandatory fields. Click the '+' symbol next to theIdentification Credentials. The Crypto Identification Credentials page is displayed.
    On the Crypto Identification Credentials page, create the crypto identification credentials for the Cloud Gateway Service.
    Specify the relevant details.
    Select the correct crypto key and the corresponding crypto certificate objects.
    Click Apply. The configuration is now added.
    Now, validate the credentials. To validate the credentials, go back to the Crypto Profile page.
    On the Crypto Profile page, click the '+' symbol next to the Validation Credentials.
    Specify the name of the object and click Apply.
    Apply changes to the Crypto and SSL Profile objects and return to the Cloud Gateway Service object definition window.
    Under Enterprise application connections, click Add and specify all the required details.
    Note: Let the value of SSL Proxy Profile remain as none, unless you need to use SSL to the application.
    Click Apply so that the changes to the allowed enterprise application connections are saved.
    On the main page of the gateway service, click Apply to apply the changes made to the gateway service and enterprise application connections.

Adding a cloud connector certificate

    On the IBM WebSphere Data Power page, go to Objects > Crypto Configuration > Crypto Service and click Add.
    On the Crypto Certificate page, specify details in the required fields. Specify the Name of the crypto object.
    In the File Name field, click Upload to upload the certificate to the cert:/// directory.
    Click Apply.

Adding the cloud connector certificate to the validation credentials certificate list

    On the IBM WebSphere Data Power page, go to Objects > Crypto Configuration > Crypto Validation Credentials.
    On the Crypto Validation Credentials page, in the Certificates field, search for the cloud crypto certificate by scrolling, and select the certificate.
    Click Add to add the selected certificate to the certificate list.
    Click Apply.

Managing secure connections - Standard Secure Connector

Since the enterprise server is behind a firewall, you will be able to access this server only through a Secure Connector. Follow the procedure given below to install and run a basic Secure Connector.
After you create a Secure Connector in the cloud, you must configure a machine behind the firewall to facilitate communication between the Secure Connector and a specific endpoint behind the firewall. Use the Secure Connector installer to configure the machine behind the firewall. Note: The machine on which you choose to run the installer must have access to the endpoint. You do not have to run the installer on the same machine as the endpoint.

To download the Secure Connector installer:

    On the Cloud Integration home page, create a new secure connection by clicking the Manage secure connections button. If you already have a secure connection, it will be listed with the existing Secure Connectors.
    If you do not have a secure connection, specify the name and description of your secure connection.
    Click the Install button of the Secure Connector that you would like to install. The links to the latest configuration and readme files are displayed. The download links for Windows (32-bit and 64-bit architecture) and Linux (32-bit and 64-bit architecture) are also displayed.
    Note: The configuration file is used to configure the Secure Connector. The readme file contains the links to the Secure Connector downloads and MD5SUM to verify the installers.
    Click the appropriate link based on your machine configuration.

    To install the Secure Connector:
    Launch the Secure Connector installer you downloaded.
        windows-secure-connector-installer-32bit.exe
        windows-secure-connector-installer-64bit.exe
        linux-secure-connector-installer-32bit.sh
        linux-secure-connector-installer-64bit.sh
    The Secure Connector Installer Wizard is displayed.
    Click Next then read and accept the licensing agreement.
    Click Next and choose an installation directory.
    Click Next. A message window states the location where the target directory will be created.
    Note: If an install directory exists, a warning message displays and you must confirm that you want to install and overwrite existing files.
    Click OK.
    Set up shortcut options to start, stop, and edit a Secure Connector.
        Select one or both of the following options:
            Create shortcuts in the Start menu.
            Create additional shortcuts on the desktop.
        Select a program group from which you will access the shortcuts.
        Choose to create shortcuts for the current user or all users.
    Click Next. The installation progress displays.
    Select a Secure Connector configuration file. If you have not already downloaded a Secure Connector configuration file, download one now.
    Click Next.
    For Windows installation, choose to install and run the Secure Connector as a Windows Service. If you choose install the Secure Connector as a Windows Service, you can control the Secure Connector using the Windows Services control panel (recommended). If you choose not to install and run the Secure Connector as a Windows Service, then the Secure Connector is installed as a Windows application. To run the Secure Connector as a Windows Service, you must specify the following service account information:
        Service Start Mode
        Service Account Domain
        Service Account User
        Service Account Password
    The Create Vendor JAR window is displayed. In the Connector column, select the connector for which you want to install additional files. Files that have already been installed are displayed in the Installed Files column.
    Click Add and select the library files to upload. In the appliance, the valid files are .jar and .dll are the valid library file types. The files that you select are displayed in the Files to Add column.
    Click Update. The files that display in the Files to Add column are not committed until you click Update.
    A confirmation dialog box is displayed. Follow the instructions in the dialog box.
    Click Next. The installation is complete.
    Click Done.

Starting and stopping Secure Connectors on Windows (Installed as a Windows Service)

    Open the Windows Services window : Start > Control Panel > Administrative Tools > Services.
    Scroll down the list of services to locate the IBM Secure Connector service.
    Right-click on the IBM Secure Connector service and select the appropriate command: Start, Stop, Pause, Resume, or Restart.

Starting and stopping Secure Connectors on Windows (Installed as a Windows Application)

    Start the Secure Connector from either the Windows Start menu shortcut or desktop shortcut.
        From the Windows Start button, select All Programs > IBM > Cast Iron Secure Connector <connector_name> > Start Secure Connector
        From the Windows desktop, click the Start Secure Connector shortcut to start the Secure Connector.
    Stop the Secure Connector from either the Windows Start menu shortcut or desktop shortcut.
        From the Windows Start button, select All Programs >IBM > Cast Iron Secure Connector <connector_name> >Stop Secure Connector.
        From the Windows desktop, click the Stop Secure Connector shortcut to stop the Secure Connector.

Starting and stopping Secure Connectors on Linux

    Start the Secure Connector from either the menu shortcut , desktop shortcut or command line. Choose one of the following options:
        Select <application> > IBM > Cast Iron® Secure Connector <connector_name> > Start Secure Connector.
        From the desktop, click the Start Secure Connector shortcut to start the Secure Connector.
        From the command prompt, enter runclient_osgi.sh start.
    Stop the Secure Connector from either the menu shortcut, desktop shortcut, or command line. Choose one of the following options:
        Select <application> > IBM > Cast Iron Secure Connector <connector_name> > Stop Secure Connector.
        From the desktop, click the Stop Secure Connector shortcut to stop the Secure Connector.
        From the command prompt, enter runclient_osgi.sh stop.

Upgrading Secure Connectors

This topic provides information about upgrading Secure Connectors.

    Create a new Secure Connector.
    Download the latest version of the Secure Connector installer, based on your operating system. For example, Windows or Linux.
    On a Windows or Linux machine, launch the Secure Connector installer. The Cast Iron Secure Connector wizard guides you through the upgrade process.
    Note: On a 32-bit or 64-bit Linux machine, you must download a 32-bit or 64-bit Secure Connector, respectively, and complete the upgrade process. You cannot upgrade to a 32-bit Secure Connector on a 64-bit Linux machine.
    Note: If you already have a Secure Connector installation that is higher than or same as the latest version, a warning message states that you have an existing installation and alternatively you can upgrade the existing installation.
    Note: You must stop the Secure Connector (if already started) before upgrading.
    Note: Before you proceed with the Secure Connector upgrade process, ensure that you have:
        Stopped the Secure Connector and corresponding projects.
        Taken a manual backup of the certificates (if any) located at <secure_connector_install_path>/etc/security or jre/lib. You may want to replace/add your certificates after upgrade.
    Click the Upgrade option. The Select the installed path list box is displayed.
    Select the Secure Connector installed path, if it is displayed in the list box. Else, click Browse button to select the installed path.
    Click Next, then read and accept the licensing agreement.
    Click Next. The installation progress is displayed. A message is displayed stating that the installation has been completed successfully. The path to the installer program is also displayed.
    Click Done.
    Start the Secure Connector.

Updating (re-configuring) the Secure Connector
If you have a new Secure Connector configuration file and you want to re-configure your secure connector, complete the steps described below:

    Launch the Secure Connector Configuration wizard. To launch the wizard:
        Windows machine: Go to Start > All Programs > IBM > Cast Iron Secure Connector <connector_name> > Secure Connector Configuration.
        Linux machine: Select <application> > IBM > Cast Iron Secure Connector <connector_name> > Secure Connector Configuration.
    The Secure Connector configuration wizard guides you through the upgrade process.
    Click Next. The current Secure Connector Configurations are displayed if the Secure Connector is already configured.
    Update the Secure Connector configuration by clicking the Previous button and then browse and select th new Secure Connector file.
    Click Next and verify the configuration settings.
    Click Next.
    Specify settings for a proxy server: Proxy Server, Proxy Port, Login ID, Login Password, and Retype Password. These parameters are only required if your network requires that the Secure Connector uses a proxy to connect to the Cast Iron® Cloud Gateway.
    The Create Vendor JAR window is displayed. In the Connector column, select the connector for which you want to install additional files. Files that have already been installed are displayed in the Installed Files column.
    Click Add and select the library files to upload. In the appliance, the valid files are .jar and .dll are the valid library file types. The files that you select are displayed in the Files to Add column.
    Click Update. The files that display in the Files to Add column are not committed until you click Update.
    A confirmation dialog box is displayed. Follow the instructions in the dialog box.
    Click Next. The upgrade is complete.
    Restart the Secure Connector.

Creating an Integration
Follow the procedure listed below to create an integration:
Note: This feature works only with the latest version of Cast Iron Live. Contact IBM Support to get access to the latest version.

    Go to the Cloud Integration home page. Click the Create Integration button. The Cast Iron Live sign on page is displayed.
    Specify your Cast Iron Live logon credentials and click Sign In. The Cloud Management Console is displayed.
    Note: On the sign-on page, you can either choose the Evaluation Version or the Production Version. If you do not have a Cast Iron Live account, you can even sign-up for an account.
    Create your required Cast Iron orchestrations. The orchestrations must be wrapped in HTTP Receive-Response request.

You have successfully created a Cast Iron Live integration.
Signing up for Cast Iron Evaluation Version

Cast Iron Live is a multi-tenant, cloud-based platform for integrating cloud and on-premise applications with enterprise systems in a hybrid environment. You can configure, run, and manage integration in the cloud without any infrastructure footprint. Each organization must have an admin who can sign-up and obtain credentials to a Cast Iron Live evaluation cloud. The admin is authorized to create accounts for users within the organization. If the other users within the organization try to sign-up, they will be provided with the contact details of the admin.
Complete the follow steps to sign-up with Cast Iron Live Evaluation version:

    Go to the Cloud Integration home page. Click the Create Integration button. The Cast Iron Live sign on page is displayed.
    Click the Sign Up link. The sign-up instructions are displayed, if you are the first to sign-up from your organization (for example the Admin).
    Click Yes, Sign Me Up.

    An email is sent to the mail address that your organization is registered with. The email contains the instructions on getting started with Cast Iron Live. This includes the username and password, system requirements, and quick tips.
    The Sign up for Cast Iron Live page displays the thank you message, system generated username, and email Id for any queries.
    Click Create Integration Now to sign in to Cast Iron Live with your newly received user credentials.

Creating Cloud Integration APIs
Follow the procedure listed below to create a new Cloud Integration API.

    On the Cloud Integration home page, you can create APIs by first setting up a secure connection and then creating an integration. For more information about adding and configuring Secure Connectors, see Managing secure connections - Standard Secure Connector and Managing the Enterprise Secure Connector. For more information about creating an integration, see Creating an Integration.
    Click the Create an Enterprise API button. The Create an Enterprise API page is displayed.
    Specify the name and description of your API.
    You can create APIs from the following:
        Enterprise Endpoint - DB2/Oracle and Enterprise Endpoint - SAP
        Cast Iron Live Orchestrations
        Bluemix Apps
    The newly created API tiles are present on the Cloud Integration page.

Creating an Enterprise API - DB2 or Oracle endpoint
Follow the procedure listed below to create an API from an Enterprise endpoint:

    Go to the Cloud Integration home page. Click the Create an Enterprise API button. The Create an Enterprise API page is displayed.
    Specify the name and description of your API.
    Click the Generate from an Enterprise Endpoint button The Resources page is displayed.
    In the Resources page, you must begin by connecting to the database you want.
    Click the dropdown under Database and select Add another Enterprise Endpoint. The Connect to a Database or SAP page is displayed.
    Select either DB2 or Oracle and specify the following details:
    Note: For on-premise applications, someone with a database administrator role on the customer's infrastructure, discusses with the integration developer about the number of users and the access permissions for each of the users. The administrator then grants those users the access required for APIs.

    The administrator can also grant the users appropriate access and privileges to database assets. For example, the database administrator can grant access to particular database tables and certain operations the users can perform on the table.
        Name of the secure connector
        Database Name
        Hostname or IP Address
        Port
        User name
        Password
    Click Connect
    Select an already existing on-premise database and select the required schema.
    After selecting the schema, select the table for which you want to create an API.
    Select the resources that you want to make available when creating the API. You can include resources such as Get, Post, Put, and Delete.
    Note: Click the copy icon available next to the resource names to view and copy the API URL.
    Click Create API. The API is successfully created with the required resources.
    Expand the resources to view the JSON examples.

    Sample JSON script:

    GET:

    Request JSON: Response JSON: { "rows": { "row": [ { "CUSTOMERID": "xs:integer", "NAME": "xs:string", "ADDRESSID": "xs:integer", "TITLE": "xs:string", "FLAG": "xs:string" } ] } }

    POST:

    Request JSON: { "rows": { "row": [ { "CUSTOMERID": "xs:integer", "NAME": "xs:string", "ADDRESSID": "xs:integer", "TITLE": "xs:string", "FLAG": "xs:string" } ] } } Response JSON: { "rows": { "rowsModifiedCount" : "xs:int" } }

    PUT:

    Request JSON: { "rows": { "row": [ { "CUSTOMERID": "xs:integer", "NAME": "xs:string", "ADDRESSID": "xs:integer", "TITLE": "xs:string", "FLAG": "xs:string" } ] } } Response JSON: { "rows": { "rowsModifiedCount" : "xs:int" } }

    DELETE:

    Request JSON: Response JSON: { "rows": { "rowsModifiedCount" : "xs:int" } }

    Go to the service instance home page. Here, you can see the newly created API.
    Click Create a Database API to create a new API for yet another database. Repeat the steps from Step 7 onwards.

You have successfully created an API from a database.
Creating an Enterprise API - SAP endpoint
Follow the procedure listed below to create an enterprise API from an SAP endpoint:

    Go to the Cloud Integration home page. Click the Create an Enterprise API button. The Create an Enterprise API page is displayed.
    Specify the name and description of your API.
    Click the Generate from an Enterprise Endpoint button The Resources page is displayed. In the Resources page, you must begin by connecting to the database you want.
    Note: If you are creating an enterprise endpoint for the first time, you must click the Connect to your first Enterprise Endpoint button.
    On the Resources page, select the Add another Enterprise Endpoint option from the Select your Enterprise Endpoint drop-down list. The Connect to a Database or SAP page is displayed.
    Click the SAP button specify the following details:
    Note: For on-premise applications, someone with a database administrator role on the customer's infrastructure, discusses with the integration developer about the number of users and the access permissions for each of the users. The administrator then grants those users the access required for APIs.

    The administrator can also grant the users appropriate access and privileges to database assets. For example, the database administrator can grant access to particular database tables and certain operations the users can perform on the table.
        Name of the secure connector
        Hostname or IP Address
        Port
        System Number
        Client
        User name
        Password
    Click Connect. Once you click connect, the database is added to the list of databases. A new field called Schema is added.
    Select an already existing on-premise database and select the required schema.
    After selecting the schema, select the table for which you want to create an API.
    Select the resources that you want to make available when creating the API. You can include resources such as Get, Post, Put, and Delete.
    Note: Click the copy icon available next to the resource names to view and copy the API URL.
    Click Create API. The API is successfully created. The details that are displayed includes the API_SECRET key, the resources and the JSON examples. The generated API_SECRET key is displayed in the API details.
    Click the copy icon to view the URL, the API_SECRET key and the user name and password to access the API.

You have successfully created an API from SAP. Your newly created SAP API tile is now present in the Cloud Integration home page.
Creating an API from Cast Iron Live Orchestrations
Follow the procedure listed below to create an API from Cast Iron Live Orchestrations:
Note: This feature works only with the latest version of Cast Iron Live. Contact IBM Support to get access to the latest version.

    Go to the Cloud Integration home page. Click the Create an API button. The Create an API page is displayed.
    Specify the name and description of your API.
    Click the Create from Cast Iron Live Orchestrations button The Cast Iron Live sign-on page is displayed.
    Specify your Cast Iron Live logon credentials and click Sign In The Resources page is displayed.
    Select the resources that you want to make available when creating the API. You can include resources such as Get, Post, Put, and Delete.
    Select the name of your project available in the cloud management console.
    Add the parameters and code sample, if required.
    Click Create API. The API is successfully created with the required resources.

You have successfully created an API from Cast Iron Live Orchestrations.
Creating an API from Bluemix applications
Follow the procedure listed below to create an API from Cast Iron Live Orchestrations

    Go to the Cloud Integration home page. Click the Create an API button. The Create an API page is displayed.
    Specify the name and description of your API.
    Click the Create from Bluemix apps button. The Resources page is displayed.
    Select the resources that you want to make available when creating the API. You can include resources such as Get, Post, Put, and Delete.
    Select the a Bluemix application from the list.
    Add the parameters and code sample, if required.
    Click Create API. The API is successfully created with the required resources.

You have successfully created an API from Bluemix applications.
Viewing APIs
The APIs that you have created are displayed as API tiles in the service console.

    Click the newly created API tile to view details about the API. The description and API resources are displayed.
    Click the arrow beside the tile to view the parameters and examples related to an API resource.

Using the API URL
The APIs created are saved in the VCAP_SERVICES as well. Complete the following steps to use the API URL

    If you are using Node.js as the runtime for your Bluemix application, use the following sample code for the Cloud Integration API:

    if (process.env.VCAP_SERVICES) { //USE FOR CLOUDFOUNDRY DEPLOYMENT var env = JSON.parse(process.env.VCAP_SERVICES); env_cloudint = env['CloudIntegration-0.1'][0].credentials; } var user = env_cloudint .userid; var password = env_cloudint .password; for (i=0; i<env_cloudint .apis.length; i++) { if (env_cloudint .apis[i].name == api_name) myurl = url.parse(env_cloudint .apis[i].url); } if (myurl == null) console.log ('API Url is not defined!'); options = { host: myurl.hostname, port: 443, path: myurl.path, secureProtocol: 'SSLv3_method', headers: {'Authorization': 'Basic ' + new Buffer (user+':'+password).toString('base64')} }; //Set the API method to be invoked options.method = 'GET'; //Make a http request var request = https.request(options, function(response) { //Response handling here });

    Make an HTTPS call using the API URL.
    Note: You can now provide a different username and password to access the on-premise database. This is an optional feature. These credentials will override the credentials provided during the API creation. You will need to pass the Username and Password as HTTP headers. If there are no USERNAME and PASSWORD passed in the headers while invoking the API, then the credentials specified during API creation would be used.

Request payload generation rules
When you provide a JSON input to the created API, conform to the following rules:

    Case 1: Passing a string value:

    Accepted format: "name" : "Varun" (double quotes only).
    Case 2: Passing inexplicit quotes in a string:

    Accepted format: "name" : "'Varun'" (The single quotes will be replaced with explicit double quotes).
    Case 3: Passing a number starting with a leading 0:

    Accepted format: "id" : "_$_0001_$_" (Any string prefixed with _s_ and post-fixed with _$_ will be treated as a number).
    Case 4: Passing a number:

    Accepted format: "age" : 30

Troubleshooting
Note: If you face any issues while creating or accessing an API, check the Cast Iron Secure Connector logs or check the DataPower logs for the DataPower secure connector. For Cast Iron Integration, check the system logs of Cast Iron in your account.
You can encounter the exception given below with Secure Connector, while connecting to the database:

com.approuter.maestro.sdk.mpi.ActivityFailedException(Connection error while getting connection out of the pool. SQLSTATE: HY000 ERRORCODE: 0 Error Message: [CastIron Systems][DB2 JDBC Driver]End of stream was detected on a read. [CastIron Systems][DB2 JDBC Driver]End of stream was detected on a read.) FaultTime:2014-05-29T10:48:40.661Z JobID:BB85F0FE3B3EBD8FDEBEDAC80AEF4956 ActivityID:4 ................... com.approuter.module.database.protocol.DBConnectionException: Connection error while getting connection out of the pool. SQLSTATE: 08001 ERRORCODE: 0 Error Message: [CastIron Systems][DB2 JDBC Driver]Error establishing socket to host and port: 9.1.2.1.:50000. Reason: Connection timed out: connect at com.approuter.module.database.protocol.ConnectionManager.getConnection(ConnectionManager.java:178) at com.approuter.module.database.activity.GenericQueryActivity.process(GenericQueryActivity.java:140) at com.approuter.module.database.activity.GenericQueryActivity.execute(GenericQueryActivity.java:107) at com.approuter.agent.container.sdk.AgentServiceManager.execute(AgentServiceManager.java:132) at com.approuter.agent.container.protocol.AgentActivityHandler.execute(AgentActivityHandler.java:346) at com.approuter.agent.container.serviceimpl.AgentServiceImpl.execute(AgentServiceImpl.java:105) at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:88) at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:55) at java.lang.reflect.Method.invoke(Method.java:618) at com.sun.xml.ws.api.server.InstanceResolver$1.invoke(InstanceResolver.

This exception occurs if the database is not reachable from the Secure Connector.
Verify that the database is accessible from the server machine where the Secure Connector is running.

How can I to use multiple Secure Connectors in a single machine?
To user multiple Secure Connectors in a single machine, complete the following steps:
You must install the new secure connections on different paths (different directories). Configure the newly installed Secure Connectors by changing the port numbers (Listen on Port and Transmit on Port). Contact with your network administrator and get new numbers for the Listen to Port and Transmit on Port fields.
AGENT_LOCKED error when starting the standard Secure Connector
If the standard secure connector is deleted from the Cloud Management Console, and a new one with the same name is created, the AGENT_LOCKED error will be thrown when starting the Secure Connector on the local machine.

If a secure connector is deleted and a new one with the same name is then created from Cloud Management Console, the secure connector configuration for the new instance is different from the original one. At this time, if the secure connector isn't updated in user's environment, the connector will still use the previous authentication key to connect to Cast Iron Live. Thus, the agent is locked by Cast Iron Live.
To resolve the problem, complete the following steps:

    Contact IBM Cloud Integration Support to unlock the secure connector from the backend.
    Re-configure the Secure Connector.
        Download a new Secure Connector configuration from Cloud Management Console.
        On Windows, run Secure Connector Configuration from the start menu to import the downloaded configuration.
        On Linux, run agent_configurator.jar from *sc_installation_path*/utils to import the downloaded configuration.
    Restart the Secure Connector.

Common errors thrown when you invoke the API

    You do not have permission to access this API.

    Solution: Ensure that you pass in the header "API_SECRET" the value for which will be specified in the API details when you created them.
    (The content of elements must consist of well-formed character data or markup.) FaultTime:2014-07-22T14:51:45.524+05:30 JobID:8BDB16C024B8B4EFCF04FC6E024C4F72 ActivityID:6796

    Solution: Verify the input HTTP header value for Content-Type. If it is 'application/xml', then the input XML input is not well formed. If it is 'application/json', then the input JSON input is not well formed.
    (An invalid XML character (Unicode: 0x7b) was found in the prolog of the document.) FaultTime:2014-07-22T14:52:26.972+05:30 JobID:AAB2AC0C96CF7BB297579046BB5D4DD3 ActivityID:6796

    Solution: Verify the input HTTP header value for Content-Type. If it is 'application/json', the JSON is not well formed or could not be converted into a valid XML. If it is 'application/xml', then the input XML input is not well formed.

Secure Connector window hangs and no information is displayed
Secure Connector window hangs and no information is displayed.

Solution: You must always run the Secure Connector as an Administrative user.
The Secure Connector installer on a 64-bit Linux machine throws error
The following error is thrown when you run the Secure Connector installer on a 64-bit Linux machine:

Invalid MIT-MAGIC-COOKIE-1 keyException in thread "main" java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11.XToolkit

Solution: To install Secure Connector on Linux , you must enable X or install VNC on Linux machines to get the Secure Connector installation wizard. After creating the connection, run the following commands to launch the UI based Secure Connector installation wizard:

sudo chmod +x linux-secure-connector-installer_64.sh sudo ./linux-secure-connector-installer_64.sh
How to set the debug value of the Secure Connector logs to True
To set the debug value of the Secure Connector logs to True, complete the following steps:

    Go to the root directory where your Secure Connector is installed.
    Open the config folder.
    Open the localConfig_ws.xml file for editing.
    Change the value of the <debug> tag to True. By default, the value of the <debug> tag is False.

