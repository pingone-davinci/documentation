# Clearbit Connector

Author: Matthew Teets


# Introduction

The Clearbit connector allows users to auto-fill registration forms and look up general information about people/businesses.

The Clearbit connector currently only has one capability that allows the user to insert an email address and, from the Clearbit API response, retrieve the following information: givenName(first name), familyName(last name), email, city, state, and country of that individual. If business information is wanted from the inserted email, printing the connectors rawResponse output parameter will display all additional data that clearbit has available.


# Setup


## Resources

#### For information and additional help, see the following sections of the Clearbit API documentation:
* Clearbit API Documentation:
   * [API Versioning](https://dashboard.clearbit.com/docs#versioning) 
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


## Setting up the connector

#### Clearbit Connector General Settings:
* Navigate to the Clearbit connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner
* Search for the desired connector (in this case, Clearbit).
* Select the Clearbit connector.
* Once the Clearbit connector has been added the _**Your Connections**_ list, click on Clearbit
* From here you will see a single text field labeled _**API Key**_
   * API Key:
      * Copy and paste your Clearbit API key into the corresponding text field.
      * Click Apply


# Using the connector in a flow

### Some Clearbit connector use cases:
* Auto-fill registration forms
   * Or any other kind of form that requires personal information
* Retrieve information on almost any person/business

### Get All User Information:
* The Clearbit connector has one capability level property which can be filled out one of 2 ways:
   * Manually inserting the email into the text field.
   * Selecting the appropriate output variable from the previous connector.
* The Clearbit connector does not generate any output on its own.
   * To see any output from the Clearbit connector you can do the following:
      * Add an HTML block after your Clearbit connector.  
      * Click on the Custom HTML Message capability
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Clearbit connector
         * Choose from any of the offered output variables


# Capabilities

Leave this section blank: it will be generated automatically


# Limitations

```
Clearbit doesn't have information on every email address. There will be instances where no information will be 
available for the Clearbit API. In this case Clearbit will return a 404 response status code. No need to worry 
because the Clearbit connector is fully equipped to gracefully handle these instances by simply returning empty 
person values.
```
