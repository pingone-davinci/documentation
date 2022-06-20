# WhatsApp for Business


## Doc draft

Author: Matthew Teets


# Introduction

You can use the WhatsApp connector to send templated messages to any WhatsApp account.

The WhatsApp connector so far has the single capability that allows the user to fillout WhatsApp templated messages, and send them from the connector to a single users WhatsApp account. The connector cannot currently receive any messsages or input from the recipient of the templated messages, but takes care of all API request and variable formatting.

You can use the WhatsApp connector to send: <br>
* Text message templates <br>
* Media message templates <br>
* Interactive message templates <br>


# Setup


## Resources

For information and setup help, see the following sections of the WhatsApp API documentation:

* WhatsApp API Documentation: <br>
   * [Send Message Template Overview](https://developers.facebook.com/docs/whatsapp/cloud-api/guides/send-message-templates)
      * [Text-Based Message Template](https://developers.facebook.com/docs/whatsapp/message-templates/creation)
      * [Media-Based Message Template](https://developers.facebook.com/docs/whatsapp/api/messages/message-templates/media-message-templates)
      * [Interactive Message Template](https://developers.facebook.com/docs/whatsapp/api/messages/message-templates/interactive-message-templates)

* DaVinci Documentation: <br>
   * [Login to DaVinci](https://portal.singularkey.com/dashboard)
   * [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
   * [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)


## Requirements

To use WhatsApp connector:
* [Overview of Required Assets](https://developers.facebook.com/docs/whatsapp/business-management-api/get-started#1--acquire-an-access-token-using-a-system-user-or-facebook-login)
   * This will help you generate the required access token.
* [Current Graph API Version](https://developers.facebook.com/docs/graph-api/)
* [Message Template Creation](https://www.facebook.com/business/help/2055875911147364?id=2129163877102343)
   * [Message Template Guidelines](https://developers.facebook.com/docs/whatsapp/message-templates/guidelines) 


## Setting up the connector

In Singular Key, add a **PingOne SSO** connection. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


## WhatsApp Connector General Settings
* Navigate to the WhatsApp connector via the connections tab.
* Click on the WhatsApp connector.
* From here you will see two text fields: Access Token and Version
   * Access Token:
      * Copy and paste your permanent access token into the corresponding text field.
   * Version:
      * The version will be filled out already.
      * Update the version if necessary.

---
### Pre-requisites for Connector
* You must have a working permanent access token.
* You must have the current version of the graph API.
* You must have a valid and approved message template.
---

# Using the connector in a flow

[Describe how to use the connector after it has been set up.]

You can use the connector in a variety of use cases, such as:


## [Use case]

[Describe how to use the connector in this use case. Does it come with a related flow template? Is there a generic use case flow to follow in the Singular Key core documentation?]


## [Use case]

[Describe how to use the connector in this use case. Does it come with a related flow template? Is there a generic use case flow to follow in the Singular Key core documentation?]


# Capabilities

Leave this section blank: it will be generated automatically


# Troubleshooting

[Optional section]


## Common solutions

[Describe solutions to common problems the user might encounter when setting up or using the connector. If there are any required steps, include them in the **Setup** section.]


## Troubleshooting resources


### [Resource description]

[Describe other resources, tools, reference information, or links that might be helpful when troubleshooting.]


### Testing capabilities

You can test each capability individually. For help, see [Testing capabilities](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


# Limitations

[Optional section]

[Describe any issues or limitations.]

