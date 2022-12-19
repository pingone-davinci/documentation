
# SendGrid Connector

Author: Kathy Khong 

# Introduction

The SendGrid connector to enhances your registration flow by enabling multiple capabilities for contact creation and email delivery.
With SendGrid, you will be able to:
  * Create a contact
  * Update an exisiting contact
  * Read a contact using an Id 
  * Import a contact job status 
  * Create a Single Send 
  * Schedule a Single Send 

  Twilio SendGrid is a cloud-based SMTP service that provides email delivery at scale, allowing you to send email without the cost and complexity of maintaining your own email servers.

  For more information, see [Twilio SendGrid Documentation.](https://docs.sendgrid.com/) 

# Setup

## Setting up the connector
In DaVinci, add a SendGrid connection. For help, see [Adding a Connection.](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html) 

## Connector Configuration 

### API Key 
You must create your first API key using the [Twilio SendGrid App.](https://signup.sendgrid.com/)

# Using the connector in a flow

Once a SendGrid connector has been added you can click to configure the connector's capabilities. 

# Capabilities

### Create or Update Contact (addOrUpdateContact)


Create a new contact or update an existing contact

#### List Ids `textField`


An array of List ID strings that this contact will be added to.

#### Email `textField` `required`


The contact's primary email. This is required to be a valid email

#### Address line 1  `textField`


The first line of the address for the contact

#### Address line 2  `textField`


A second line of the address for the contact

#### Alternate emails `textField`


Additional email(s) associated with the contact

#### City `textField`


The contact's city

#### Country `textField`


The contact's country. Can be a full name or an abbreviation.

#### First name `textField`


The contact's personal name

#### Last name  `textField`


The contact's family name

#### Postal code `textField`


The contact's ZIP code or other postal code

#### State, province, or region `textField`


The contact's state, province, or region.

---

### Get contact by email (getContactByEmail)


Retrieve a contact using an email

#### Email `textField` `required`


The contact's primary email. This is required to be a valid email

---

### Get contact by id (getContactById)


Retrieve a contact using a the contact id

#### Id `textField` `required`


The contact's id

---

### Delete a contact (deleteContact)


Delete a contact

#### Id `textField` `required`


The contact's id

#### Delete all contacts `toggleSwitch`


Must be set to 'true' to delete all contacts.  default: None

---

### Import Contact Status (importContactStatus)


Check the status of a contact import job using a job id 

#### Job id  `textField`


 Indicates that the contacts are queued for processing. 

---

### Create single send  (createSingleSend)


Create a new single send

#### Name `textField` `required`


The name of the Single Send

#### Categories `textField`


The categories to associate with the Single Send

#### Send at `textField`


The ISO 8601 time at which to send the Single Send. This must be in future or the string 'now'. Emails can be scheduled up to 72 hours in advance. However, this scheduling constraint does not apply to campaigns sent via Marketing Campaigns.ISO 8601 time format (yyyy-MM-ddTHH:mm:ssZ) using the required send_at field. For example, the ISO 8601 format for 9:00 AM UTC on May 6, 2020 would be 2020-05-06T09:00:00Z. You may also pass the string 'now' to send the Single Send immediately.

#### List Ids `textField`


An array of List ID strings that this contact will be added to.

#### Segment ids `textField`


The recipient Segment Ids that will receive the Single Send. Max items: 10

#### Send all `toggleSwitch`


Set to true to send to All Contacts. If set to false, at least one list Ids or segment Ids value must be provided before the Single Send is scheduled to be sent to recipients

#### Subject `textField`


The subject line of the Single Send. Do not include this field when using a Design Id.

#### HTML content `textArea`


The HTML content of the Single Send. Do not include this field when using a Design Id.

#### Plain Content `textArea`


The plain content of the Single Send. Do not include this field when using a Design Id.

#### Generate Plain Content `toggleSwitch`


If set to true, Plain Content is always generated from HTML Content. If set to false, Plain Content is not altered.

#### Design Id  `textField`


A Design Id can be used in place of HTML Content, , and/or subject. You can retrieve a design's Id from the 'List Designs' endpoint or by pulling it from the design's detail page URL in the Marketing Campaigns App.

#### Editor `textField`


The editor — 'design' or 'code' — used to modify the Single Send's design in the Marketing Campaigns App.  default: code Allowed Values: code, design

#### Suppression Group Id  `textField`


The Id of the Suppression Group to allow recipients to unsubscribe 

#### Custom unsubscribe url `textField`


The URL allowing recipients to unsubscribe

#### Sender Id `textField`


 The Id of the verified Sender. You can retrieve a verified Sender's Id from the 'Get Verified Senders' endpoint or by pulling it from the Sender's detail page URL in the SendGrid App.

#### IP pool `textField`


The name of the IP Pool from which the Single Send emails are sent.

---

### Schedule a single send  (scheduleSingleSend)


Schedule a Single Send for future delivery using a single send id

#### Send at `textField`


The ISO 8601 time at which to send the Single Send. This must be in future or the string 'now'. Emails can be scheduled up to 72 hours in advance. However, this scheduling constraint does not apply to campaigns sent via Marketing Campaigns.ISO 8601 time format (yyyy-MM-ddTHH:mm:ssZ) using the required send_at field. For example, the ISO 8601 format for 9:00 AM UTC on May 6, 2020 would be 2020-05-06T09:00:00Z. You may also pass the string 'now' to send the Single Send immediately.

#### Single Send Id `textField` `required`


The  Id of a Single Send 

---



# Troubleshooting 

## Common solutions

### Error when deleting a contact
Only one of Ids OR Delete all contacts should be set, not both.

### Error when scheduling a Single Send using a Single Send Id
Single Send email config must have either a custom unsubscribe url OR suppression group id to schedule. In additon, the email config HTML Content  and Sender Id must contain a valid value to be able to schedule the Single Send. 



### Testing capabilities

You can test each capability individually. For help, see [Testing capabilities](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


# Limitations

[Optional section]

[Describe any issues or limitations.]

