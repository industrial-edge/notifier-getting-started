# Configuration

- [Configuration](#configuration)
  - [Configure PLC Connection](#configure-plc-connection)
    - [Databus](#databus)
    - [OPC UA Connector](#opc-ua-connector)
  - [Configure Data Service](#configure-data-service)
  - [Configure Notifier](#configure-notifier)
    - [Create notification rules](#create-notification-rules)
    - [Manage "My notifications"](#manage-my-notifications)
    - [Show user list](#show-user-list)
    - [Show user groups](#show-user-groups)
    - [Send notification via email](#send-notification-via-email)
  - [Connect smart devices](#connect-smart-devices)
    - [Setup Notifier mobile app](#setup-notifier-mobile-app)

## Configure PLC Connection

To read data from the PLC and provide the data, we will use the OPC UA Connector to establish a connection with the PLC via OPC UA. The Connector transfers the data to the Databus.

In order to build this infrastructure, these apps must be running and configured properly:

- Databus
- OPC UA Connector

### Databus

Go to the IEM App and open the Databus Configurator.

Create an user and add a suitable topic to receive the data from the connector and deploy the configuration.

![1](/docs/graphics/1_Databus.PNG)

### OPC UA Connector

Go to the IEM App and open the OPC UA Connector Configurator.

Add your PLC as data source and deploy the configuration.

![2](/docs/graphics/2_Connector.PNG)

## Configure Data Service

The Data Service can be enabled to receive the PLC data, that was transferred by the connector. The user can configure all needed parameters structured by assets. These assets are then accessible within the Notifier.

For detailled instructions please refer to [using the Data Service](https://github.com/industrial-edge/data-service).

Finally the Data Service configurations should look like this:

![3](/docs/graphics/3_DataService.PNG)

## Configure Notifier

### Create notification rules

The asset structure, including all parameters that were created above, is now available within the Notifier. That allows the user to create the following notification rules based on these parameters:

- Information: Production was stopped
- Warning: High gas consumption
- Alert: Error within production

**Create an ***information*** rule**

Go to the IED Web UI and launch the Notifier.

Navigate to Settings > Manage notification rules on the left bar.

Below the asset tree, select the dedicated asset for the notification rule.

Click "Add notification rule" to create the first rule "Production was stopped" as an information.

Configure the following settings and save.

![5_1](/docs/graphics/5_1_Notifier.PNG)

**Create a ***warning*** rule**

Click "Add notification rule" to create the second rule "High gas consumption" as a warning.

Configure the following settings and save.

![5_2](/docs/graphics/5_2_Notifier.PNG)

**Create an ***alert*** rule**

Click "Add notification rule" to create the third rule "Error within production" as an allert.

Configure the following settings and save.

![5_2](/docs/graphics/5_3_Notifier.PNG)

Finally the configuration should look like this:

![5_Notifier_Overview](/docs/graphics/5_Notifier_Overview.PNG)

### Manage "My notifications"

Navigate to Settings > Manage "My notifications" on the left bar.

Here you can create filters for displaying only your notifications, which can be selected on the "Notifications" start page.

> Hint: For showing notifications on a **smart device**, these filters must be configured necessarily for a user. Otherwise no notifications are send to the smart device!

The filter conditions can be related to the notification type (information/wargning/alert) or the asset.

For displaying all notifications, the configuration could look like this:

![6_My_Notifications](/docs/graphics/6_My_Notifications.PNG)

### Show user list

Navigate to Settings > User list on the left bar.

Here the administrator gets an overview of currently registered users within the Notifier app. The administrator is able to edit and delete an user account.

In general users are managed on the Edge Device. In the screen "My User Groups", you can enable access to the Notifier app which is installed on the Edge Device. To do this, you create groups with different authorizations and provide dedicated users access to the Notifier.

![6_User_List](/docs/graphics/6_User_List.PNG)

### Show user groups

Navigate to Settings > User groups on the left bar.

Here the administrator gets a list of user groups within the Notifier app. The administrator is able to create a new group to send notifications to a group of users.

The way of notification can be configured as push notification or email. Additionally you can configure a time that may pass before an escalation is triggered and the next user is notified.

If a group contains several users, these are notified in the specified order. If one user can not accept the notification within the configured time, the notification is forwarded to the next one.

![6_User_Roles_2](/docs/graphics/6_User_Roles_2.PNG)

![6_User_Roles_3](/docs/graphics/6_User_Roles_3.PNG)

### Send notification via email

You can also send the notifications displayed under "My notifications" by email. 

![6_SMTP_3](/docs/graphics/6_SMTP_3.PNG)

To do so, you must first configure the SMTP settings and then enable the "Email" option in the filter settings.

**Configure SMTP settings**

Navigate to Settings > Configure SMTP settings on the left bar.

Enter the server details and choose an option for authentication.

![6_SMTP_1](/docs/graphics/6_SMTP_1.PNG)

To test the configuration, click "Validate configuration" and a dedicated window opens. Click "Send Email" to receive a test email to the address configured in the "To" field.

![6_SMTP_2](/docs/graphics/6_SMTP_2.PNG)

![6_SMTP_4](/docs/graphics/6_SMTP_4.PNG)

**Enable email option**

Navigate to Settings > Manage "My notifications" on the left bar.

Add at least one filter for displaying your notifications.

Activate the "Email" option and save.

## Connect smart devices

It is also possible to receive notifications from the IED on a smart device. Therefore the SIMATIC Notifier mobile app must be installed on the smart device. The mobile app supports iOS and Androis devices (smartphones/tablets) as well as Wear OS devices (smartwatch). The app can be downloaded from the dedicated app stores.

To be able to receive push notifications from the Notifier, you need to set up a connection from your smart device to the IED. Please consider the following preconditions:

- the Notifier app is installed and running on the IED
- the Notifier mobile app is installed on your smart device
- both devices are connected to the same network (WLAN)
- communication ports are opened (443, 51883)

### Setup Notifier mobile app

Here we use an iPhone with iOS operating system, the Notifier app was downloaded from the Apple app store and installed on the smartphone.

Open the Notifier app on your smart device. 

Click "Add connection" and select "Edge" as connection type.

![7_iOS_1](/docs/graphics/7_iOS_1.png)    ![7_iOS_2](/docs/graphics/7_iOS_2.png)

Enter the login data from your Edge Device and click "Login".

![7_iOS_3](/docs/graphics/7_iOS_3.png)

After successful login, activate the heartbeat settings. This prevents a disconnection from the server when the app is minimized. On Android smart devices this function is called "Keep connection".

![7_iOS_4](/docs/graphics/7_iOS_4.png)

Afterwards enable push notifications to receive incoming notifications at all times.

![7_iOS_5](/docs/graphics/7_iOS_5.png)

Now the smart device is ready to receive notifications from the dedicated IED.

Please switch to the [Usage](/README.md#usage) chapter, to see how to work with the Notifier and it's dedicated mobile app.
