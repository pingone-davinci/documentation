
# Freshdesk Connector

Author: Matthew Teets

# Introduction
Freshdesk is a help desk platform that provides customer support solutions. Our intent is to enable the ability to automate help desk tasks into your identity flows.

### Capabilities:

##### Ticket Capabilities
* `Create Ticket`
* `View Ticket`
* `Update Ticket`
* `Delete Ticket`

##### Contact Capabilities
* `Create Contact`
* `View Contact`
* `Update Contact`
* `Delete Contact`


# Setup

## Resources

#### For information and additional help, see the following sections of the Freshdesk API documentation:
Freshdesk Capabilities API Documentation:
   * [Freshdesk API Reference](https://developers.freshdesk.com/api/)

Ticket Capabilities
  * [Create Ticket](https://developers.freshdesk.com/api/#create_ticket)
  * [View Ticket](https://developers.freshdesk.com/api/#view_a_ticket)
  * [Update Ticket](https://developers.freshdesk.com/api/#update_ticket)
  * [Delete Ticket](https://developers.freshdesk.com/api/#delete_a_ticket)

Contact Capabilities
  * [Create Contact](https://developers.freshdesk.com/api/#create_contact)
  * [View Contact](https://developers.freshdesk.com/api/#view_contact)
  * [Update Contact](https://developers.freshdesk.com/api/#update_contact)
  * [Delete Contact](https://developers.freshdesk.com/api/#hard_delete_contact)

   
DaVinci Documentation:
  * [Login to DaVinci](https://portal.singularkey.com/dashboard)
  * [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
  * [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)


## Requirements

#### To use the Freshdesk connector:
* You must have access to a Freshdesk Support Portal.
   * Sign up for an account [here](https://support.freshdesk.com/en/support/signup)
        * Your account must be upgraded to the Growth plan (at the very least).
* You must have a valid API key in order to make any calls to the Freshdesk API.
   * Find your Freshdesk API key [here](https://support.freshdesk.com/en/support/solutions/articles/215517)

## Setting up the connector

#### Freshdesk Connector General Settings:
* Navigate to the Freshdesk connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner.
* Search for the desired connector (in this case, Freshdesk).
* Select the Freshdesk connector.
* Once the Freshdesk connector has been added the _**Your Connections**_ list, click on the connector.
* From here you will see two text fields labeled Freshdesk API Key and Freshdesk API Version.
   * **Freshdesk API Key**:
      * Before pasting your API key into the text field you must first base64 encode the key with 'X'
        * E.g. ` echo -n 'WnbxdMY444lF2gwM3fDx:X'| base64 ` = ` V25ieGRNWTQ0NGxGMmd3TTNmRHg6WA== `
            * The above command is for the Mac Terminal
      * Copy and paste your base64 encoded API Key into the text field.
   * **Freshdesk API Version**:
      * This field will already be filled out.
         * Only change this if the API version is out of date.
   * `Click Apply`

# Using the connector in a flow

### Some Freshdesk connector use cases:
* Submit a new support ticket to Freshdesk 
* Resolve an open ticket
* Create a new user account to the support portal
* Remove contacts from the support portal

### Freshdesk API Request Requirements:
* You must have a fully functioning and configured Freshdesk Support Portal.
* Both the **Freshdesk API Key** and **Freshdesk API Version** text fields must be filled in the connector settings.

---

### Simple Use Case - submit a new support ticket to Freshdesk:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Freshdesk connector and select the `Create Ticket` capability.
* This Freshdesk capability has five capability level properties that can be filled out 1 of 2 ways:
   1. Manually inserting the desired values into the respective text fields.
   2. Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* `Email` is simply the email address of the requester.
    * If no contact exists with this email address in your Freshdesk portal, it will be added as a new contact.
* `Subject` is the subject of the ticket.
* `Description` is the HTML content of the ticket.
* `Priority` is simply the priority of the ticket. The default value is set to 1.
    |Priority|Value|
    |---|---|
    |Low|1|
    |Medium|2|
    |High|3|
    |Urgent|4|
* `Status` is simply the status of the ticket. The default value is set to 2.
    |Status|Value|
    |---|---|
    |Open|2|
    |Pending|3|
    |Resolved|4|
    |Closed|5|
* The Freshdesk connector does not generate any output on its own.
   * To see the HTTP response object returned the Freshdesk API you can do the following:
      * Add an HTTP block after your Freshdesk connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Freshdesk connector option with the `Create Ticket` capability listed.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

### Simple Use Case - resolve an open ticket:
* Add the Freshdesk connector to the desired flow and select the `Update Ticket` capability.
* This Freshdesk capability has five capability level properties that can be filled out 1 of 2 ways:
   1. Manually inserting the desired values into the respective text fields.
   2. Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* `Ticket ID` is the ticket number listed next to the ticket title in the Freshdesk tickets tab.
    * E.g. `Computer won't turn on #23`
        * 23 would be the ticket ID
##### The following properties can be changed using this capability
* `Subject` is the subject of the ticket.
* `Description` is the HTML content of the ticket.
* `Priority` is simply the priority of the ticket. The default value is set to 1.
    |Priority|Value|
    |---|---|
    |Low|1|
    |Medium|2|
    |High|3|
    |Urgent|4|
* `Status` is simply the status of the ticket. The default value is set to 2.
    |Status|Value|
    |---|---|
    |Open|2|
    |Pending|3|
    |Resolved|4|
    |Closed|5|
* To update an open ticket to a resolved ticket, change the `Status` to 4.
    * Click `Apply`
* The Freshdesk connector does not generate any output on its own.
   * To see the HTTP response object returned the Freshdesk API you can do the following:
      * Add an HTTP block after your Freshdesk connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Freshdesk connector option with the `Update Ticket` capability listed.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

### Simple Use Case - create a new user account:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Freshdesk connector and select the `Create Contact` capability.
* This Freshdesk capability has five capability level properties that can be filled out 1 of 2 ways:
   1. Manually inserting the desired values into the respective text fields.
   2. Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* `Email` is the primary email address of the contact.
* `Name` is the first and last name of the new contact.
* `Job Title` is the job title of the contact.
* `Phone Number` is the telephone number of the contact.
* `Address` is the current address of the contact.
* The Freshdesk connector does not generate any output on its own.
   * To see the HTTP response object returned the Freshdesk API you can do the following:
      * Add an HTTP block after your Freshdesk connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Freshdesk connector option with the `Create Contact` capability listed.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

### Use Case - delete a contact from Freshdesk:
* Add the Freshdesk connector to the desired flow and select the `Delete Contact` capability.
* This Freshdesk capability has one capability level property.
* `Contact ID` is the identification number generated by Freshdesk.
* This text field can be filled out 1 of 2 ways:
   1. Manually inserting the contact id (also known as a requester id) into the respective text fields.
        * This method can only be done if you have access to the JSON response object containing the desired contact id.
   2. Selecting the appropriate output variable from a previous connector via the angle bracket button ( **{}** ).
      * Once the angle bracket button has been pressed select the Freshdesk connector option that says `Create Contact` and then select `contactId` under the output object tab.
* The Freshdesk connector does not generate any output on its own.
   * To see the HTTP response object returned the Freshdesk API you can do the following:
      * Add an HTTP block after your Freshdesk connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Freshdesk connector option with the `Delete Contact` capability listed.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

# Capabilities

### Create Ticket (createTicket)


A ticket is an issue raised by a requester that needs to be solved

#### Email `textField` `required`


Email address of the requester. If no contact exists with this email address in Freshdesk, it will be added as a new contact

#### Subject `textField` `required`


Subject of the Freshdesk ticket

#### Description `textField` `required`


HTML content of the ticket

#### Priority `textField` `required`


Priority of the ticket. The default value is 1

#### Status `textField` `required`


Status of the ticket. The default value is 2

---

### View Ticket (viewTicket)


View one existing ticket, or all existing tickets

#### Ticket ID `textField` `required`


The numerical ID of the desired ticket. Can be found manually in your Freshdesk portal (i.e. 5 is the ID for “Ticket Title #5”)

---

### Update Ticket (updateTicket)


Make updates to an existing ticket

#### Ticket ID `textField` `required`


The numerical ID of the desired ticket. Can be found manually in your Freshdesk portal (i.e. 5 is the ID for “Ticket Title #5”)

#### Subject `textField` `required`


Subject of the Freshdesk ticket

#### Description `textField` `required`


HTML content of the ticket

#### Priority `textField` `required`


Priority of the ticket. The default value is 1

#### Status `textField` `required`


Status of the ticket. The default value is 2

---

### Delete Ticket (deleteTicket)


Delete an existing ticket

#### Ticket ID `textField` `required`


The numerical ID of the desired ticket. Can be found manually in your Freshdesk portal (i.e. 5 is the ID for “Ticket Title #5”)

---

### Create Contact (createContact)


A contact is a customer or a potential customer who has raised a support ticket through any channel

#### Email `textField` `required`


Email address of the requester. If no contact exists with this email address in Freshdesk, it will be added as a new contact

#### Name `textField`


First and last name of the new contact

#### Job Title `textField`


Job title of the contact

#### Phone Number `textField`


Telephone number of the contact

#### Address `textField`


Address of the contact

---

### View Contact (viewContact)


View a contact who raised a support ticket

#### Contact ID `textField` `required`


The "contactId" listed under the output object

---

### Update Contact (updateContact)


Update a contact who raised a support ticket

#### Contact ID `textField` `required`


The "contactId" listed under the output object

#### Name `textField`


First and last name of the new contact

#### Job Title `textField`


Job title of the contact

#### Phone Number `textField`


Telephone number of the contact

#### Address `textField`


Address of the contact

---

### Delete Contact (deleteContact)


Hard delete a contact to completely remove it from the portal. Can be used for GDPR compliance

#### Contact ID `textField` `required`


The "contactId" listed under the output object

---


