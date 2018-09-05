*Quick links :*
[Home](README.md) - [IoT Platform Starter](CREATEIOTP.md) - [Device Types and Devices](DISCOVERYDEVICE.md) - [Node-RED Setup](NODERED.md) - [Sensor Data](DISCOVERYIOTDATA.md) - [Node-RED Charts](DASHBOARD.md) - [Store Data in Cloud Storage](CLOUDANT.md) - [Historical Charts](HISTORY.md) - [Watson Studio](STUDIO.md) - [Jupyter Notebooks](JUPYTER.md)
***

# Receive Device Environmental Sensor Data in Node-RED

## Lab Objectives

In this lab you will build a flow that receives Device environmental temperature and humidity sensor data.  You will learn:

- How to create a new Node-RED flow and configure IoT Nodes
- How to output the Device environmental temperature and humidity data.
- How to work with JSON data and observe the sensor results in the Debug sidebar.

### Introduction

In just a few nodes, Node-RED can receive the data that was transmitted from the device over MQTT to Watson IoT Platform.  This simple exercise will be the foundation for the next several sections that plot the data in a dashboard, trigger Real Time threshold alerts, store the data in Cloud Storage and allow for data analytics and anomaly detection.

### Step 1 - Configure an IoT in Node

- From the Input category of the left Node-RED palette, select an **ibmiot node** and drag it onto your Node-RED flow (1).
- Double-click on the IBM IoT node. An **Edit ibmiot in node** sidebar will open.
- Configure the Authentication dropdown to **Bluemix Service** (2).
- Uncheck All and set the Device Type to **DiscoveryKit** (3).
- Check All Device Ids (4)
- Uncheck All and set the Event to **status** (5).
- Click on the red **Done** button.
 ![Receive DiscoveryKit Data](screenshots/DiscoveryKit-ReceiveData-IoTnode.png)

### Step 2 - Extract the Temperature from the JSON Object

- Recall that the environmental sensor data was transmitted in a JSON object

 ```
 { "d": {"temperature":T,"humidity":H,"pressure":B,"proximity":D,"acc_x":X,"acc_y":Y,"acc_z":Z,"gyr_x":X,"gyr_y":Y,"gyr_z":Z,"mag_x":X,"mag_y":Y,"mag_z":Z} }
 ```

- Node-RED passes data from node to node in a *msg.payload* JSON object.
- The **Switch** node can be used to test if the msg.payload.d.temperature is not null.
- From the Function category of the left Node-RED palette, select a **Switch** node and drag it onto your Node-RED flow (6).
- Double-click on the Switch node. An **Edit switch node** sidebar will open.
- Set the "Property" field to *payload.d.temperature* (7).
- From the dropdown, select **is not null** (8)
- Click on the red **Done** button.
 ![Receive DiscoveryKit Data](screenshots/DiscoveryKit-ReceiveData-Switchnode.png)

- The **Change** node can be used to extract a particular value so that it can be directly output or manipulated (for instance in a Dashboard chart which we will take advantage of in the next section).
- From the Function category of the left Node-RED palette, select a **Change** node and drag it onto your Node-RED flow (9).
- Double-click on the Change node. An **Edit change node** sidebar will open.
- Configure the "to" AZ dropdown to msg. and set it to *payload.d.temperature* (10).
- Click on the red **Done** button.
 ![Receive DiscoveryKit Data](screenshots/DiscoveryKit-ReceiveData-Changenode.png)

## Step 3 - Node-RED Debug Nodes

- Debug nodes can be used to print out JSON object values and help you validate your program.
- From the Output category of the left Node-RED palette, drag two **debug nodes** onto your Node-RED flow (11).
- Double-click on one of them. An **Edit debug node** sidebar will open.
- Configure the Output to print the *complete msg object* (12).
- Click on the red **Done** button.
 ![Receive DiscoveryKit Data](screenshots/DiscoveryKit-ReceiveData-Debugnode.png)

### Step 4 - Wire the Node-RED nodes together

- Wire the Node-RED nodes together by click / dragging your mouse from nodelet to nodelet as show in the screenshot.
- Click on the red **Deploy** button in the upper right corner.
- Observe the DiscoveryKit IoT Node sensor data in the **debug** tab of the Node-RED right sidebar.  You can expand the twisties to expose the JSON object information. Hover over a debug message in the right sidebar and the node that generated the message will be outlined in orange.
  ![Receive DiscoveryKit Data](screenshots/DiscoveryKit-ReceiveData-Deploy.png)

**Congratulations** - Your Node-RED flow is receiving sensor data from the Discovery Kit board.

Continue to the next step - [Node-RED Charts](DASHBOARD.md)
***
*Quick links :*
[Home](README.md) - [IoT Platform Starter](CREATEIOTP.md) - [Device Types and Devices](DISCOVERYDEVICE.md) - [Node-RED Setup](NODERED.md) - [Sensor Data](DISCOVERYIOTDATA.md) - [Node-RED Charts](DASHBOARD.md) - [Store Data in Cloud Storage](CLOUDANT.md) - [Historical Charts](HISTORY.md) - [Watson Studio](STUDIO.md) - [Jupyter Notebooks](JUPYTER.md)
***
