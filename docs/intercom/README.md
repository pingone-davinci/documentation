
# Intercom Connector

Author: Matthew Teets

# Introduction
Intercom specializes in business messaging and offers companies an open line of communication with their clients.

### Capabilities:

##### Contact Capabilities
* `Create Contact`
* `View Contact`
* `Update Contact`
* `Delete Contact`
* `Create Contact Note`

##### Conversation Capabilities
* `Create Conversation`
* `View Conversation` 

##### Messages Capabilities
* `Create Messages`

##### Custom Capabilities
* `Make Custome API Call`

# Setup

## Resources

#### For information and additional help, see the following sections of the Intercom API documentation:
Intercom Capabilities API Documentation:
   * [Intercom API Reference](https://developers.intercom.com/intercom-api-reference/reference/welcome)

Contact Capabilities
  * [Create Contact](https://developers.intercom.com/intercom-api-reference/reference/create-a-contact)
  * [View Contact](https://developers.intercom.com/intercom-api-reference/reference/retrieve-a-contact)
  * [Update Contact](https://developers.intercom.com/intercom-api-reference/reference/update-a-contact)
  * [Delete Contact](https://developers.intercom.com/intercom-api-reference/reference/delete-a-contact)
  * [Create Contact Note](https://developers.intercom.com/intercom-api-reference/reference/create-a-note-for-contact)

Conversation Capabilities
  * [Create Conversation](https://developers.intercom.com/intercom-api-reference/reference/create-a-conversation)
  * [View Conversation](https://developers.intercom.com/intercom-api-reference/reference/retrieve-a-conversation)

Messages Capabilities
  * [Create Message](https://developers.intercom.com/intercom-api-reference/reference/create-a-message)
   
DaVinci Documentation:
  * [Login to DaVinci](https://portal.singularkey.com/dashboard)
  * [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
  * [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)


## Requirements

#### To use the Intercom connector:
* You must have access to a configured Intercom account.
   * Or make a new account [here](https://app.intercom.com/admins/sign_in).
* You must also have access to a configured Intercom App.
	* Or make a new Intercom application [here](https://developers.intercom.com/building-apps/docs).
* You must have a valid API key in order to make any calls to the Intercom API.
   * Instructions to find your Intercom API key [here](https://developers.intercom.com/building-apps/docs/authentication-types#access-tokens).

## Setting up the connector

#### Intercom Connector General Settings:
* Navigate to the Intercom connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner.
* Search for the desired connector (in this case, Intercom).
* Select the Intercom connector.
* Once the Intercom connector has been added to the _**Your Connections**_ list, click on the connector.
* From here you will see an empty text field labeled Intercom Access Token.
   * **Intercom Access Token**:
      * Copy and paste your Intercom Access Token into the text field.
	   * `Click Apply`

# Using the connector in a flow

### Some Intercom connector use cases:
* Send an admin message to a specific contact.
* Create a new user or lead in your contact list.
* Attach a comment/note to a contact.

### Intercom API Request Requirements:
* You must have a fully functioning and configured Intercom Application/Workspace.
* The **Intercom Access Token** text fields must be filled in the connector settings.

---

### Simple Use Case - send an admin message to a specific contact:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow, then click save.
* Once inside the flow sandbox add the Intercom connector and select the `Create Message` capability.
* This Intercom capability has three capability level properties that can be filled out 1 of 2 ways:
   1. Manually inserting the desired values into the respective text fields.
   2. Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* `Message Body` is the contents of the message.
  * This is sent as plain text.
* `Type` is the role associated to the contact (User or Lead).
* `Contact Email` is the email address associated with the desired customer.
* The Intercom connector does not generate any output on its own.
   * To see the HTTP response object returned by the Intercom API you can do the following:
      * Add an HTTP block after your Intercom connector. 
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Intercom connector option with the `Create Message` capability listed.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

# Capabilities

Leave this section blank: it will be generated automatically
