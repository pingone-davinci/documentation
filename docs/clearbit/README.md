# Clearbit Connector

Author: Matthew Teets


# Introduction

The Clearbit connector allows users to look up and return general information about a person/business. All capabilities and use cases revolve around gathering specific public information on an individual through their personal/business email address.  
       
The Clearbit connector comes with 3 capabilities that the user is able to start operating out of the box.    

### Capabilities:
* `Get All User Information`
* `Email Risk Score`
* `Make Custom API Call`


# Setup


## Resources

#### For information and additional help, see the following sections of the Clearbit API documentation:
* Clearbit API Documentation:
   * [Enrichment API](https://dashboard.clearbit.com/docs#enrichment-api)
      * [Combined API](https://dashboard.clearbit.com/docs#enrichment-api-combined-api)
      * [Person API](https://dashboard.clearbit.com/docs#enrichment-api-person-api)
      * [Email lookup](https://dashboard.clearbit.com/docs#enrichment-api-person-api-email-lookup)
   * [Risk API](https://dashboard.clearbit.com/docs#risk-api)
      
* DaVinci Documentation: <br>
   * [Login to DaVinci](https://portal.singularkey.com/dashboard)
   * [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
   * [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)


## Requirements

#### To use the Clearbit connector:
* You must first create an account with Clearbit.
   * Create an account [here](https://dashboard.clearbit.com/signup)
* You then must be able to locate and copy your account API Key.
   * Access your account API key [here](https://dashboard.clearbit.com/api)
* Next it is wise to check if the your API version is still up to date.
   * Check API version [here](https://dashboard.clearbit.com/docs#versioning)


## Setting up the connector

#### Clearbit Connector General Settings:
* Navigate to the Clearbit connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner.
* Search for the desired connector (in this case, Clearbit).
* Select the Clearbit connector.
* Once the Clearbit connector has been added the _**Your Connections**_ list, click on Clearbit.
* From here you will see two text fields labeled API Key, Person API Version, and Risk API Version.
   * **API Key**:
      * Copy and paste your Clearbit API key from the Clearbit API reference into the corresponding text field.
   * **Person API Version**:
      * This field will already be filled out.
         * Only change this if the API version is out of date.
   * **Risk API Version**:
      * This field will already be filled out.
         * Only change this if the API version is out of date.
   * `Click Apply`

# Using the connector in a flow

### Some Clearbit connector use cases:
* Auto-fill registration forms.
* Obtain general information about an individual.
* Obtain information about a potential client's company.
* Obtain information about a competitors company.
* Verify the legitimacy of an email and IP address.
* If an email and IP address are suspicious initiate additional sign-on steps.

---

### Use Case - obtain general information about an individual:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Clearbit connector and choose the `Get All User Info` capability.
* This Clearbit connector capability has a single capability level property that can be filled out 1 of 2 ways:
   * Manually inserting the desired email into the text field.
   * Selecting an appropriate output email variable from the previous connector.
      * E.g. an HTTP connector with an HTML form that prompts the user to enter an email.
* The Clearbit connector does not generate any output on its own.
   * To see the information retrieved by the Clearbit connector you can do the following:
      * Add an HTTP block after your Clearbit connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Clearbit connector.
         * Choose from any of the offered output variables.
            * Format, repeat, and add as many output variables as desired.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

### Use Case - verify the legitimacy of an email and IP address:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Clearbit connector and choose the `Email Risk Score` capability.
* This Clearbit connector capability has 3 capability level properties that can be filled out 1 of 2 ways:
   * Manually inserting the desired email, IP address, and full name into the text field.
   * Selecting the appropriate output variables from a previous connector.
      * E.g. an HTTP connector with an HTML form that prompts the user for the required info.
* The Clearbit connector does not generate any output on its own.
   * To see the information retrieved by the Clearbit connector you can do the following:
      * Add an HTTP block after your Clearbit connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Clearbit connector.
         * Choose from any of the offered output variables.
         * Risk Output Variables:
            * riskLevel
            * riskScore
            * riskReasons
         * Format, repeat, and add as many output variables as desired.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

### Use Case - obtain a formatted JSON object with all person data:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Clearbit connector and choose the `Make Custom API Call` capability.
* This Clearbit connector capability has 6 capability level properties that can be manually filled out:
   * **Domain Name**: 
      * Used to call a specific API within the Clearbit API.
         * E.g. `person, company, person-stream, company-stream.`
   * **Endpoint**:  
      * Used to call a specific operation from inside the Clearbit API.
         * E.g. `/combined/find?email=alex@clearbit.com.`
   * **Method**:
      * Specifies the HTTP CRUD request.
         * E.g. `GET, POST, PUT, DELETE, PATCH.`
   * **Query Parameters**:
      * The kye-value pairs that appear after the question mark in the URL.
         * E.g. `email=usename@mail.com, name=John Smith, company=PingIdentity`.
   * **Headers**:
      * Key-value pairs that represent the meta-data associated with the Clearbit API request and response.
         * E.g. `Authorization: Bearer gk_5hid2f0b97d45d05add2b, Content-Type: application/json`.
   * **Body**: 
      * Used to manually craft a JSON request body for the Clearbit API.
* The Clearbit connector does not generate any output on its own.
   * To see the information retrieved by the Clearbit connector you can do the following:
      * Add an HTTP block after your Clearbit connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Clearbit connector.
         * Choose from any of the offered successful response output variables.
            * rawResponse
            * statusCode
            * headers
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

# Capabilities

Leave this section blank: it will be generated automatically


# Limitations

```
Clearbit doesn't have information on every email address. There will be instances where no information will be 
available from the Clearbit API. In this case Clearbit will return a 404 response status code. No need to worry 
because the Clearbit connector is fully equipped to gracefully handle these instances by simply returning empty 
person values.
```
