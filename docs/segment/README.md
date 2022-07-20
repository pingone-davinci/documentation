
# Segment Connector

Author: Matthew Teets


# Introduction

Using the software and API from Segment, this connector collects, organizes, and cleans your customer data.
       
The Segment connector comes loaded with 7 capabilities that the user is able to start operating out of the box.

### Capabilities:
* `Identify`
* `Track`
* `Page`
* `Screen`
* `Group`
* `Alias`
* `Make Custom API Call`

# Setup


## Resources

#### For information and additional help, see the following sections of the Segment API documentation:
* Segmet API Documentation:
   * [HTTP Tracking API Source](https://segment.com/docs/connections/sources/catalog/libraries/server/http-api/)
      * [Identify](https://segment.com/docs/connections/sources/catalog/libraries/server/http-api/#identify)
      * [Group](https://segment.com/docs/connections/sources/catalog/libraries/server/http-api/#group)
      * [Track](https://segment.com/docs/connections/sources/catalog/libraries/server/http-api/#track)
      * [Page](https://segment.com/docs/connections/sources/catalog/libraries/server/http-api/#page)
      * [Screen](https://segment.com/docs/connections/sources/catalog/libraries/server/http-api/#screen)
      * [Alias](https://segment.com/docs/connections/sources/catalog/libraries/server/http-api/#alias)
   
* DaVinci Documentation: <br>
   * [Login to DaVinci](https://portal.singularkey.com/dashboard)
   * [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
   * [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)


## Requirements

#### To use the Segment connector:
* You must first sign up for a free account and workspace with Segment.
   * Create an account [here](https://app.segment.com/signup)
* You then must locate and copy your account Write Key.
   * Access the Write Key [here](https://segment.com/docs/getting-started/02-simple-install/#find-your-write-key)
* Segment requires a Basic Auth Header to be passed with the API request.
   * View setup instructions [here](https://segment.com/docs/connections/sources/catalog/libraries/server/http-api/#headers)
* To collect data using Segment you must have a source.
   * View source setup instructions [here](https://segment.com/docs/getting-started/implementation-guide/#add-a-source)
* Segment offers testing and debugging tools to easily confirm that your API calls are being successfully sent to the source.
   * View testing and debugging instructions [here](https://segment.com/docs/getting-started/implementation-guide/#testing-and-debugging)

## Setting up the connector

#### Segment Connector General Settings:
* Navigate to the Clearbit connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner.
* Search for the desired connector (in this case, Segment).
* Select the Segment connector.
* Once the Segment connector has been added the _**Your Connections**_ list, click on Segment.
* From here you will see two text fields labeled Write Key and HTTP Tracking API Version.
   * **Write Key**:
      * Copy and paste your, now base 64 encoded, Segment Write Key into the text field.
         * Only insert the encoded Write Key into the text field.
   * **HTTP Tracking API Version**:
      * This field will already be filled out.
         * Only change this if the API version is out of date.
   * `Click Apply`

# Using the connector in a flow

### Some Segment connector use cases:
* Collect data on a user as they journey through the different branches of a flow.
* Collect data on what buttons are being pressed on a website.
* Collect data on what webpages are being viewed on a website.
* Collect data on what screens are being viewed in a mobile app.
* Collect data on what groups/teams a specific user is involved in.
* Create/Update/Combine user traits and characteristics.

---

### Use Case - create a user to track through a flow:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Segment connector and choose the `Identify User` capability.
* This Segment connector capability has two capability level properties that can be filled out 1 of 2 ways:
   * Manually inserting the desired values into the fields.
   * Selecting the appropriate output variable from a previous connector.
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* The `User ID` is a custom, user-defined string that is used to identify a specific user.
   * E.g. 1, 001, #0001, etc.
      * All characters are acceptable.
* The `Key Value List` is used as to define traits about the user.
   * Clicking on the `+` button adds a key value field.
      * **Key**: key of a key-value pair in the traits object.
      * **Value**: value of a key-value pair in the traits object.
* The Segment connector does not generate any output on its own.
   * To see the HTTP response object sent by Segment you can do the following:
      * Add an HTTP block after your Segment connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Segment connector.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

```
This connector can now be used to define a user that can be tracked through a flow.
```

---

### Use Case - track a defined user to through a flow:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Segment connector and choose the `Track User` capability.
* This Segment connector capability has three capability level properties that can be filled out 1 of 2 ways:
   * Manually inserting the desired values into the fields.
   * Selecting the appropriate output variable from a previous connector.
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* The `User ID` is a custom, user-defined string that is used to identify a specific user.
   * E.g. 1, 001, #0001, etc.
      * All characters are acceptable.
   * `In most cases this will be a user that has already been created.`
* The `Event` field is a user-defined string that is used to identify a specific event.
   * E.g. Button Clicked, Item Purchased, Added Item to Cart, etc...
      * These are events triggered by user interaction
* The `Key Value List` is used as to define properties about the event.
   * E.g. | key = item | value = Chocolate Bar |
   * Clicking on the `+` button adds a key value field.
      * **Key**: key of a key-value pair in the traits object.
      * **Value**: value of a key-value pair in the traits object.
* The Segment connector does not generate any output on its own.
   * To see the HTTP response object sent by Segment you can do the following:
      * Add an HTTP block after your Segment connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Segment connector.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

```
This connector can now be used to track the frequency of certain events through a flow.
```

---

`FINISH THIS USE CASE`       
           
### Use Case - track what webpages a user visits through a flow:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Segment connector and choose the `Track User` capability.
* This Segment connector capability has three capability level properties that can be filled out 1 of 2 ways:
   * Manually inserting the desired values into the fields.
   * Selecting the appropriate output variable from a previous connector.
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* The `User ID` is a custom, user-defined string that is used to identify a specific user.
   * E.g. 1, 001, #0001, etc.
      * All characters are acceptable.
   * `In most cases this will be a user that has already been created.`
* The `Event` field is a user-defined string that is used to identify a specific event.
   * E.g. Button Clicked, Item Purchased, Added Item to Cart, etc...
      * These are events triggered by user interaction
* The `Key Value List` is used as to define properties about the event.
   * E.g. | key = item | value = Chocolate Bar |
   * Clicking on the `+` button adds a key value field.
      * **Key**: key of a key-value pair in the traits object.
      * **Value**: value of a key-value pair in the traits object.
* The Segment connector does not generate any output on its own.
   * To see the HTTP response object sent by Segment you can do the following:
      * Add an HTTP block after your Segment connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Segment connector.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

```
This connector can now be used to track the frequency of certain events through a flow.
```

---

# Capabilities

Leave this section blank: it will be generated automatically


# Limitations

```

```
