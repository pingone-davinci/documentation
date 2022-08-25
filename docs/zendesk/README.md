
# Zendesk Connector
  

Author: Scott Banducci (scottbanducci@pingidentity.com)


# Introduction

Zendesk is award-winning customer service software trusted by 200K+ customers. Make customers happy via text, mobile, phone, email, live chat, social media. The Zendesk Connector enables you to:

1. Create Ticket
2. Read Ticket
3. Update Ticket
4. Delete Ticket
5. Comment on a Ticket
6. Create User
7. Read User
8. Update User
9. Delete User
10. Add User to Organization
11. Remove User from Organization
12. Make Custom API Call


# Setup


## Resources

For information and setup help, see the following sections of the Amazon documentation:

* [Zendesk API Reference](https://developer.zendesk.com/api-reference/ " Overview page for Zendesk API Reference")

* [Zendesk Dev Page](https://developer.zendesk.com/documentation"Zendesk Dev Landing Page. Search here for articles on using API if the API Reference is unhelpful.")


## Requirements


To use the connector, you'll need:

* A Zendesk Account
* Your Zendesk subdomain (ex. **{subdomain}**.zendesk.com)
* The email used as 'username' for the Zendesk user. NOTE: This will be used for all calls once you configure the connector.

* Your Zendesk API Token. this can be found by going to the admin center (admin center->Apps&Integrations->Zendesk API)

## Setting up the connector

  

In DaVinci, add a **zendesk** connection via the "Connections" tab. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings
  

Once you've added the connection click on its logo, or click the "**·****·****·**"  button and "Edit".

You will see the connector's details pop-up. On the GENERAL tab, enter in your

1) subdomain
2) userEmail
3) API Token

and click apply. This ensures that whenever you use this connector in a flow you will not have to reenter enter this information.


# Using the connector in a flow


The Zendesk connector allows you to use all API capabilities listed in Introduction.

First, add the Zendesk connector via the "Connections" tab (remember to setup your subdomain, userEmail and API Token). In the DaVinci Flow Studio add a Zendesk connector. Then choose the capability you'd like to use it for. You will then need to select the parameters from previous nodes in the flow (ex. an HTML form), or manually input values, in order to populate the fields.


## [Create Ticket](https://developer.zendesk.com/api-reference/ticketing/tickets/tickets/#create-ticket "Create Ticket Documentation")

Simply add the Zendesk connector node to your flow and select the Create Ticket capability.

The only required value is **Comment**. All others can be populated or left blank. 

The connector will allow you to access the ticket object that is returned via it's **ticket** output.   

## [Read Ticket](https://developer.zendesk.com/api-reference/ticketing/tickets/tickets/#show-ticket "Show Ticket Documentation")

Also known as "Show Ticket".

Add the Zendesk connector node to your flow and select the Read Ticket capability.

The only value, which is required, is **Ticket ID**.

The connector will allow you to access the ticket object that is returned via it's **ticket** output.   

##  [Update Ticket](https://developer.zendesk.com/api-reference/ticketing/tickets/tickets/#update-ticket "Update Ticket Documentation")


Add the Zendesk connector node to your flow and select the Update Ticket capability.

The only value, which is required, is **Ticket ID**. All other fields are optional. 

The connector will allow you to access the ticket object that is returned via it's **ticket** output and the audit object that is returned via it's **audit** output.


## [Delete Ticket](https://developer.zendesk.com/api-reference/ticketing/tickets/tickets/#delete-ticket "Delete Ticket Documentation")

Add the Zendesk connector node to your flow and select the Delete Ticket capability.

The only value, which is required, is **Ticket ID**.

There is no content returned from this API call but it will return "status 204" if successful and 4** if not.  


## [Comment on a Ticket](https://developer.zendesk.com/api-reference/ticketing/tickets/tickets/#update-ticket "Update Ticket Documentation")

Add the Zendesk connector node to your flow and select the Comment on a Ticket capability.

The only values, which are required, is **Ticket ID** and **comment**.

NOTE: this function uses the same API call as **Update Ticket**. The only difference is this capability only accepts a **comment** field and thus can't change any other Ticket properties.


## [Create User](https://developer.zendesk.com/api-reference/ticketing/users/users/#create-user "Create User Documentation")

Add the Zendesk connector node to your flow and select the Create User capability.

The **email** field and **external ID** must be unique among your Users, **locale** must be BCP-47 compliant, and all ID-related values (such as Organization ID) must be valid.

If you need to create users without sending out a verification email, turn on the **Verified Email** toggle.

NOTE: if no **Role** is selected the default value will be set to **end-user**.


## [Read User](https://developer.zendesk.com/api-reference/ticketing/users/users/#show-user "Show Ticket Documentation")

Also known as "Show User".

Add the Zendesk connector node to your flow and select the Read Ticket capability.

The only value, which is required, is **User ID**.

The connector will allow you to access the user object that is returned via it's **user** output.   

## [Update User](https://developer.zendesk.com/api-reference/ticketing/users/users/#update-user "Update User Documentation")

Add the Zendesk connector node to your flow and select the Update User capability.

The only required value is **User ID**. All other fields optional. 

The connector will allow you to access the user object that is returned via it's **user** output.

## [Delete User](https://developer.zendesk.com/api-reference/ticketing/users/users/#delete-user "Delete User Documentation")


Add the Zendesk connector node to your flow and select the Delete User capability.

The only value, which is required, is **User ID**.

There is no content returned from this API call but it will return "status 204" if successful and 4** if not.  


## [Create Organization Membership](https://developer.zendesk.com/api-reference/ticketing/organizations/organization_memberships/#create-membership "Create Organization Membership Documentation")

Add the Zendesk connector node to your flow and select the Create Organization Membership capability.

The only values, which are both required, are **User ID** and **Organization ID**.

The connector will allow you to access the organization_membership object that is returned via it's **organizationMembership** output.
 
## [Delete Organization Membership](https://developer.zendesk.com/api-reference/ticketing/organizations/organization_memberships/#delete-membership "Delete Organization Membership Documentation")

Add the Zendesk connector node to your flow and select the Delete Organization Membership capability.

The only value, which is required, is **Organization Membership ID**.


There is no content returned from this API call but it will return "status 204" if successful and 4** if not.  
# Capabilities
  

# Troubleshooting

NOTE: For any field in the connector which has a codeblock for input, you must enter the correct syntax of the array, object, etc. that the Zendesk API requires (see links to documentation if uncertain.)

NOTE: If there exists an Integer based field that contains an ID number such as Organization ID or Group Id, the API call will fail if this is not valid. 

NOTE: All "Toggles" represent boolean values. Off is False, On is True.

NOTE: The Make Custom API Call allows you to call any endpoint this connector does not have a built-in capability for. 

# Limitations

This connector currently cannot upload files as attachments to comments. If you would like this feature to be implemented in a future version of this connector, please let your Ping contact know.
