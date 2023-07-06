# Configuration

- [Configuration](#configuration)
  - [Configure PLC Connection](#configure-plc-connection)
    - [Databus](#databus)
    - [OPC UA Connector](#opc-ua-connector)
  - [Configure Data Service](#configure-data-service)
  - [Configure Notifier](#configure-notifier)
    - [Create notification rules](#create-notification-rules)
    - [Manage 'My notifications'](#manage-my-notifications)
  - [Configure Notifier mobile app](#configure-notifier-mobile-app)

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

On the left bar navigate to Settings > Manage notification rules.

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

### Manage 'My notifications'

Navigate to Settings > Manage 'My notifications' on the left bar.

Here you can create filters for displaying only your notifications, which can be selected on the "Notifications" start page.

| Hint: For showing notifications on a smart device, these filters must be configured necessarily for a user. Otherwise no notifications are send to the smart device!

The filter conditions can be related to the notification type (information/wargning/alert) or the asset.

For displaying all notifications, the configuration could look like this:

![6_My_Notifications](/docs/graphics/6_My_Notifications.PNG)

## Configure Notifier mobile app

The smart device shows the notifications that were selected using the "My notifications" filter criteria.

Open the Notifier iOS app and click "Add connection" to select a connection.

![5_3](/docs/graphics/Notifier_iOS_add_connection.PNG)

Select "Edge" as the connection.

![5_4](/docs/graphics/Notifier_iOS_choose_connection.PNG)

Enter the login data from your Edge and click "Login" to confirm the data.

![5_5](/docs/graphics/Notifier_iOS_add_connection_login_data.PNG)

Activate the heartbeat to get a sound if there is a connection to the server.

![5_7](/docs/graphics/Notifier_iOS_use_heartbeat.PNG)

Under "Notifications" you can see the incoming warnings and information according to the rules you have created in the Edge Notifier app. The notifications can also be acknowledged in this view.

![5_6](/docs/graphics/Notifier_iOS_overview_warning.PNG)
