# Clearbit Connector

Author: Matthew Teets


# Introduction

The Clearbit connector allows users to auto-fill registration forms and look up general information about people/businesses.

The Clearbit connector currently has one capability that allows the user to insert a person's email address and, from the Clearbit API response, return the following information about the individual: 
- givenName (first name)
- familyName (last name)
- email
- city
- state
- country

If business information is wanted from the inserted email, printing the connectors 'rawResponse' output parameter will display all additional data that clearbit has available about that individual.


# Setup


## Resources

#### For information and additional help, see the following sections of the Clearbit API documentation:
* Clearbit API Documentation:
   * [Enrichment API](https://dashboard.clearbit.com/docs#enrichment-api)
      * [Combined API](https://dashboard.clearbit.com/docs#enrichment-api-combined-api)
      * [Person API](https://dashboard.clearbit.com/docs#enrichment-api-person-api)
      * [Email lookup](https://dashboard.clearbit.com/docs#enrichment-api-person-api-email-lookup)
      
* DaVinci Documentation: <br>
   * [Login to DaVinci](https://portal.singularkey.com/dashboard)
   * [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
   * [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)


## Requirements

#### To use the Clearbit connector:
* [Create a clearbit account](https://dashboard.clearbit.com/signup)
* [Account API key](https://dashboard.clearbit.com/docs#authentication)
* [API Version](https://dashboard.clearbit.com/docs#versioning)


## Setting up the connector

#### Clearbit Connector General Settings:
* Navigate to the Clearbit connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner
* Search for the desired connector (in this case, Clearbit).
* Select the Clearbit connector.
* Once the Clearbit connector has been added the _**Your Connections**_ list, click on Clearbit
* From here you will see two text fields labeled _**API Key**_ and _**Version**_
   * API Key:
      * Copy and paste your Clearbit API key into the corresponding text field.
   * Version:
      * This field is already filled out
         * Only change if API version is out of date
    * Click Apply

# Using the connector in a flow

### Some Clearbit connector use cases:
* Auto-fill registration forms
   * Or any other kind of form that requires personal information
* Retrieve information on a potential customers business
* Retrieve information on a competitors business

### Get All User Information:
* The Clearbit connector has one capability level property which can be filled out 1 of 2 ways:
   * Manually inserting the email into the text field.
   * Selecting the appropriate output variable from the previous connector.
* The Clearbit connector does not generate any output on its own.
   * To see the output from the Clearbit connector you can do the following:
      * Add an HTML block after your Clearbit connector.  
      * Click on the Custom HTML Message capability
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Clearbit connector
         * Choose from any of the offered output variables
            * Repeat as many times as desired
      * Click apply
* In the upper right hand corner click Save, Deploy, and Run

# Capabilities

Leave this section blank: it will be generated automatically


# Limitations

```
Clearbit doesn't have information on every email address. There will be instances where no information will be 
available from the Clearbit API. In this case Clearbit will return a 404 response status code. No need to worry 
because the Clearbit connector is fully equipped to gracefully handle these instances by simply returning empty 
person values.
```
