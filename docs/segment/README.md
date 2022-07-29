
# Segment Connector

Author: Matthew Teets


# Introduction

Using the software and APIs from Segment, this connector collects, organizes, and cleans your customer data.
       
The Segment connector comes loaded with 7 capabilities that the user is able to start operating out of the box.

### Capabilities:
* `Identify`
* `Group`
* `Track`
* `Page`
* `Screen`
* `Alias`
* `Make Custom API Call`

# Setup


## Resources

#### For information and additional help, see the following sections of the Segment API documentation:
* Segment Capabilities API Documentation:
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
* Collect data on what groups/teams a specific user is in.
* Create/Update/Combine user traits and characteristics.

### Segment API Request Requirements:
* The User ID is required to send successful requests.
* Each capability has a specific characteristic that must be filled out.
   * `Track User` must have an Event string or character.
   * `Page User Is On` must have a Page Name string or character.
   * `Screen User Is On` must have a Screen Name string or character.
   * `Identify User's Group` must have a Group ID string or character.
   * `Alias` must have a Previous User ID string or character and a User ID string or character.

---

### Use Case - create a user to track through a flow:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Segment connector and choose the `Identify User` capability.
* This Segment connector capability has two capability level properties that can be filled out 1 of 2 ways:
   * Manually inserting the desired values into the fields.
   * Selecting the appropriate output variable from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* The `User ID` is a custom, user-defined string that is used to identify a specific user.
   * E.g. 1, 001, #0001, etc.
      * All characters are acceptable.
* The `Key-Value List` is used to define traits about the user.
   * E.g. 
        |     Key     |           Value           |  
        | --- | --- |
        |    email    |     example@email.com     |
   * Clicking on the `+` button adds a key-value field.
      * **Key**: key of a key-value pair in the Segment traits object.
      * **Value**: value of a key-value pair in the Segment traits object.
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
This connector can now be used to define/update information about a user as they navigate through a flow.
```

---

### Use Case - track a defined user to through a flow:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Segment connector and choose the `Track User` capability.
* This Segment connector capability has three capability level properties that can be filled out 1 of 2 ways:
   * Manually inserting the desired values into the fields.
   * Selecting the appropriate output variable from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* The `User ID` is a custom, user-defined string that is used to identify a specific user.
   * E.g. 1, 001, #0001, etc.
      * All characters are acceptable.
   * In most cases this will be a user that has already been created.
* The `Event` field is a user-defined string that is used to identify a specific event.
   * E.g. Button Clicked, Item Purchased, Item Added to Cart, etc...
      * These are events triggered by user interaction
* The `Key Value List` is used as to define properties about the event.
   * E.g. 
        |     Key     |      Value      |  
        |  --- | ---  |
        |    item     |     Chocolate Bar |
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
           
### Use Case - create custom API call:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Clearbit connector and choose the `Make Custom API Call` capability.
* This Segment connector capability has 5 capability level properties that can be manually filled out:
   * **Endpoint**:  
      * Used to call a specific operation from inside the Segment API.
         * E.g. `identify, group, track, page, screen, alias`
   * **Method**:    
      * Specifies the HTTP CRUD request.
         * E.g. `GET, POST, PUT, DELETE, PATCH.`
   * **Parameters**:    
      * The kye-value pairs that appear in the Segment traits and properties objects.
         * E.g. `email=usename@mail.com, name=John Smith, company=PingIdentity`.
      * This is also where you must specify the required key-value pairs for each endpoint. 
      * The following key names must be used for the corresponding endpoint.
         * E.g. 
          * group:
               |     Key     |      Value      |  
               |  --- | ---  |
               |    `groupId`     |     5     |
          * track:
               |     Key     |      Value      |  
               |  --- | ---  |
               |    `event`     |     Purchase Button Clicked     |
          * page:
               |     Key     |      Value      |  
               |  --- | ---  |
               |    `name`     |     Home Page     |
          * screen:
               |     Key     |      Value      |  
               |  --- | ---  |
               |    `name`     |     Home Screen     |
          * alias:
               |     Key     |      Value      |  
               |  --- | ---  |
               |    `previousId`     |    0001     |
      * Once the required endpoint key-value pair is setup you can add as many additional descriptor pairs as desired.
         * The only endpoint that doesn't have a required pair is the identify endpoint.
   * **Headers**:    
      * Key-value pairs that represent the meta-data associated with the Segment API request and response.
         * E.g. ` Content-Type: application/json`
            * These aren't visible frrom the Segment request object found in the Segment workspace 
   * **Body**:   
      * Used to manually craft a JSON request body for the Segment API.
* The Segment connector does not generate any output on its own.
   * To see the information retrieved by the Segment connector you can do the following:
      * Add an HTTP block after your Segment connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Segment connector.
         * Choose from any of the offered successful response output variables.
            * rawResponse
            * statusCode
            * headers
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

# Capabilities

Leave this section blank: it will be generated automatically
