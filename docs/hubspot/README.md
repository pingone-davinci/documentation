
# Hubspot Connector
  

## Doc draft


Author: Scott Banducci (scottbanducci@pingidentity.com)


# Introduction

Hubspot is a provider of software products for CRM, CMS, inbound marketing, sales, and customer service needs. Their platform offers a free, robust alternative to other, more costly solution providers. The Hubspot connector for Davinci enables you to:

1. Create a Contact
2. Read a Contact
3. Update a Contact
4. Archive a Contact
5. Associate a Contact with an Object
6.  Create a Ticket
7. Update a Ticket
8. Read a Ticket
9. Archive a Ticket
10. Associate a Ticket with an Object 
  

# Setup


## Resources

For information and setup help, see the following sections of the Hubspot documentation:

* [Hubspot Private-App API Documentation](https://developers.hubspot.com/docs/api/private-apps "API Overview page")

* [Contacts API documentation](https://developers.hubspot.com/docs/api/crm/contacts "Contact documentation and endpoints")

* [Tickets API documentation](https://developers.hubspot.com/docs/api/crm/tickets "Tickets documentation and endpoints")


## Requirements


To use the connector, you'll need:

* A Hubspot Account

* Your store's Private-App's bearer Token. To generate: Hubspot account homepage -> Settings -> Integrations -> Private Apps

## Setting up the connector

  

In Davinci, add a **Hubspot** connection via the "Connections" tab. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings
  

Once you've added the connection click on its logo, or click the "**·****·****·**"  button and edit.

You will see the connector's details pop-up. On the GENERAL tab, enter in your

1) bearer token

and click apply. This ensures that whenever you use this connector you will not have to reenter enter this information.


# Using the connector in a flow


The Hubspot connector allows you to create, read, update, archive and associate your Contacts or Tickets as part of your flow.

In the Davinci Flow Studio add a Hubspot connector (remember to setup your bearer token). Then choose the capability you'd like to use it for (create, read, update, archive, associate). You will then need to select the parameters from previous nodes in the flow (ex. an HTML form) to populate the fields.


## Creating/Updating a Contact or Ticket

If you want to automate the creation/update of a Contact or Ticket in Hubspot you can use this connector. Creates a Contact/Ticket with the information entered or updates the information entered. Careful about duplicate information, **especially email**.
  

## Read a Contact/Ticket

If you want to return all the contact/ticket information by ID number use the Read Contact or Read Ticket capability.   
    

## Archive a Contact/Ticket

Moves target Contact or Ticket to archive. This is Hubspot's version of Delete. 
  

## Associate a Contact/Ticket with an Object
  

If you want to create an Association between a Contact or Ticket and an Object. For example, if a ticket is created without an Association and you'd like to automate associating it with a certain company, use the Associate capabilities. You will need a few things:

- the Contact/Ticket ID number
- the toObject type (ex. Company)
- the toObject ID number (ex. 8923061577)
- the association Type (ex. 1, 2, 3, ticket_to_company, 4, contact_to_company, etc.)
  

# Capabilities
  

# Troubleshooting

  

NOTE: that the Hubspot API will respond with an empty JSON when successfully **archived** (with code: 204 No Content). 

NOTE: that the Hubspot API will respond with the raw the Contact or Ticket JSON object.

NOTE: that the following Hubspot fields have default values that can be text or numbers (recommend using numbers for un-configured test accounts):
- pipeline name, 
- pipeline status,
- association type

NOTE: the private app bearer Token must be set up for the entire connector. You can do this by clicking on the connector on the Connections page.


# Limitations

  

* Not suitable for batch operations (this connector does not allow the following: List all, Create Multiple, Archive all, etc.)
* This connector was not built to allow interactions with archived objects. All relevant calls include (archived: "false"). 
