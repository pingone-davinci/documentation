# Salesforce Cloud Marketing

Author: Balu Nagar

# Introduction

Salesforce Marketing Cloud is a marketing automation platform. The DaVinci connector will allow admins to export user data to Salesforce Marketing Cloud.

-You can use this Salesforce Marketing Cloud connector to:
-Create a new contact in Salesforce Marketing Cloud.
-Update an existing contact in Salesforce
-Read an existing contact in Salesforce
-Delete a contact in Salesforce
-Send a new message to multiple recipients.
-Send a new email message.
-Send a new SMS message to one or more mobile numbers.

# Setup

## Resources

For information and setup help, see the following documentation:
Salesforce Marketing Cloud
Salesforce Marketing Cloud documentation: https://developer.salesforce.com/docs/marketing/marketing-cloud/overview
DaVinci documentation:
Adding a connection: https://docs.pingidentity.com/csh?context=davinci_adding_a_connection
Importing a flow from the Flow Library: https://docs.pingidentity.com/csh?context=davinci_importing_a_flow_from_the_flow_library

## Requirements

To use the connector, you'll need:

1. A Salesforce Marketing Cloud URL (https://YOUR_SUBDOMAIN.rest.marketingcloudapis.com).
2. The Token for accessing the Salesforce Marketing Cloud APIs and SDKs.

## Setting up the connector

In Singular Key, add a **PingOne SSO** connection. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

# Using the connector in a flow

This Salesforce Marketing Cloud is an ITSM (IT Service Management) software and from this connector, you can perform the following:
Create a new contact in Salesforce Marketing Cloud.
Update an existing contact in Salesforce Marketing Cloud
Read an existing contact in Salesforce Marketing Cloud
Delete a contact in Salesforce Marketing Cloud
Send a new message to multiple recipients.
Send a new email message.
Send a new SMS message to one or more mobile numbers.

No special flow configuration is needed. Add the capability you want and populate its properties according to the help text.

For capabilities that have a Query Parameters section, you can add any query parameters that are supported by the Salesforce Marketing Cloud API. For help, see the Salesforce Marketing Cloud platform REST API documentation.

# Capabilities

### Create Contact (createContact)


Create a new contact in Salesforce Marketing Cloud.

#### Contact Key `textField`


Primary address for the contact, such as "acruz@example.com". Change @example.com to a valid domain.

#### Attribute Sets `codeEditor`


Array of information used to create a new contact or update existing contact. Example - "{ "name": "Email Addresses", "items": [{ "values": [{ "name": "Email Address", "value": "acruz@example.com" }, { "name": "HTML Enabled", "value": true }] }] }".

---

### Update Contact (updateContact)


Update an existing contact in Salesforce Marketing Cloud.

#### Contact Key `textField`


Primary address for the contact, such as "acruz@example.com". Change @example.com to a valid domain.

#### Attribute Sets `codeEditor`


Array of information used to create a new contact or update existing contact. Example - "{ "name": "Email Addresses", "items": [{ "values": [{ "name": "Email Address", "value": "acruz@example.com" }, { "name": "HTML Enabled", "value": true }] }] }".

---

### Read Contact (readContact)


Read an existing contact in Salesforce Marketing Cloud.

#### Contact Keys `textField`


String array of one or more contact keys. Example - "Key1", "Key2".

---

### Delete Contact (deleteContact)


Delete a contact in Salesforce Marketing Cloud.

#### Contact Keys `textField`


String array of one or more contact keys. Example - "Key1", "Key2".

---

### Send Push Notification (sendPushNotification)


Send a new message to multiple recipients.

#### Definition Key `textField`


The unique identifier of the definition. Example - "Push Transactional API 1".

#### Recipients `codeEditor`


contains parameters and metadata for the recipient. such as - "{ "contactKey": "recipient1", "messageKey": "f0d8enf0d0snd", "attributes": { "FirstName": "John", "NonRecipientDynamicDefinitionAttribute": "5" } }" or  "{ "to": ["DeviceToken1OfRecipient2", "DeviceToken2OfRecipient2"], "messageKey": "hd846bsbfk037b", "attributes": { "FirstName": "Doe" } }".

#### Content `codeEditor`


Content of the SMS. Example - "{ "title": "New Title", "subtitle": "New Subtitle", "message": "This is the overridden message" }".

#### Attributes `codeEditor`


The information that personalizes the message for the request, written as key-value pairs. Example - "{ "Purpose": "Sample" }".

#### Options `textField`


Other options. like - { badge: '1' }.

---

### Send Email (sendEmail)


Send a new email message.

#### Object ID or Key `textField`


Object ID of the entry event send definition that comes from the response when creating a TriggeredSendDefinition. Either objectID or the external key is required.

#### From `codeEditor`


Object containing email address and name of sender. Example - "{ "Address": "code@exacttarget.com", "Name": "Code@" }".

#### To `codeEditor`


Object requiring email address and optional subscriber parameters passed in at send time. Example - "{ "Address": "example@example.com", "SubscriberKey": "example@example.com", "ContactAttributes": { "SubscriberAttributes": { "Region": "West", "City": "Indianapolis", "State": "IN" } } }".

#### Options `testField`


Object used to specify asynchronous or synchronous. If not specified, defaults to asynchronous. Example - "{ "RequestType": "ASYNC"}".

---

### Send SMS message (sendSMSMessage)


Send a new SMS message to one or more mobile numbers.

#### Id `textField`


The encoded message ID.

#### Subscribers `codeEditor`


Array of up to 250 subscriber records where the message is sent to. Subscribers is different from mobileNumbers. Example - "{ "MobileNumber": "15555554410", "SubscriberKey": "ExampleSubKey1", "Attributes":{ "FirstName": "Michael" } }".

#### Subscribe `textField`


Flag to indicate a subscription should be created if none exist. True or False.

#### Resubscribe `textField`


Flag to indicate a subscription should be reset if currently unsubscribed. True or False

#### Keyword `textField`


The keyword must align with code on message. Required when subscribe and/or resubscribe are true. Such as - "JOINSMS".

#### Override `textField`


Flag to indicate that the contact is receive the messageText as provided instead of the message's original text. True or False

#### Message Text `textField`


Text value to be used in place of the message's original text. This value is required when override is true.

#### BlackoutWindow `codeEditor`


Details about the window of time where messages should not be sent. Following values - UtcOffset, WindowStart, WindowEnd.

#### Send Time `textField`


Date and Time in UTC that the message will go out. Example format: 2012-10-17 17:01. 

#### ContentURL `textField`


The URL of the media content sent via an MMS message.

---


### Testing capabilities

You can test each capability individually. For help, see [Testing capabilities](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).
