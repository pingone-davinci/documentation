
# Mailchimp Transactional Connector

Author: Matthew Teets


# Introduction

This Mailchimp connector allows the user to configure recipient settings, monitor account activity, and send transactional emails containing information on purchases by leveraging the Mailchimp Transactional (Mandrill) API.

### Capabilities:
* `Send Transactional Email`
* `Add Email to Allowlist`
* `Remove Email from Allowlist`
* `Add Email to Denylist`
* `List Account Senders`
* `Make Custom API Call`


# Setup

## Resources

#### For information and additional help, see the following sections of the Mailchimp Transactional API documentation:
* Mailchimp Capabilities API Documentation:
   * [Transactional API Source](https://mailchimp.com/developer/transactional/api/)
      * [Send Transactional Email](https://mailchimp.com/developer/transactional/api/messages/send-new-message/)
         * [In-depth look](https://mailchimp.com/developer/transactional/guides/send-first-email/)
      * [Add Email to Allowlist](https://mailchimp.com/developer/transactional/api/allowlists/add-email-to-allowlist/)
      * [Remove Email from Allowlist](https://mailchimp.com/developer/transactional/api/allowlists/remove-email-from-allowlist/)
      * [Add Email to Denylist](https://mailchimp.com/developer/transactional/api/rejects/add-email-to-denylist/)
      * [List Account Senders](https://mailchimp.com/developer/transactional/api/users/list-account-senders/)
   
* DaVinci Documentation: <br>
   * [Login to DaVinci](https://portal.singularkey.com/dashboard)
   * [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
   * [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)


## Requirements

#### To use the Mailchimp Transactional connector:
* You must have a Mailchimp Transactional account.
   * Create an account [here](https://login.mailchimp.com/signup/)
* You must also have a valid API Key in order to make any calls to the Transactional API.
   * Generate a new API Key [here](https://mandrillapp.com//settings)
* You then need to add the domain that you will be sending your emails from.
   *  Learn more on how to add your domain [here](https://mailchimp.com/developer/transactional/guides/send-first-email/#add-a-sending-domain)
* You will need to configure your DNS records to enable [DKIM](https://en.wikipedia.org/wiki/DomainKeys_Identified_Mail) and [SPF](https://en.wikipedia.org/wiki/Sender_Policy_Framework)
   * Learn how to configure your DNS records [here](https://mailchimp.com/developer/transactional/guides/send-first-email/#configure-your-dns)
* You will need to then verify ownership of your domain.
   * Verification documentation [here](https://mailchimp.com/developer/transactional/guides/send-first-email/#verify-domain-ownership)

## Setting up the connector

#### Mailchimp Connector General Settings:
* Navigate to the Mailchimp connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner.
* Search for the desired connector (in this case, Mailchimp).
* Select the Mailchimp connector.
* Once the Mailchimp connector has been added the _**Your Connections**_ list, click on the connector.
* From here you will see two text fields labeled Transactional API Key and Transactional API Version.
   * **Transactional Key**:
      * Copy and paste your API Key into this text field.
   * **Transactional API Version**:
      * This field will already be filled out.
         * Only change this if the API version is out of date.
         * Check the API version in the request URL's found [here](https://mailchimp.com/developer/transactional/api/)
            * Example: `https://mandrillapp.com/api/1.0/allowlists/add`
               * The version here is 1.0
   * `Click Apply`

# Using the connector in a flow

### Some Mailchimp Transactional connector use cases:
* Password reset emails 
* Purchase confirmation emails 
* Forum activity
* Shipping update/notification emails

### Mailchimp Transactional API Request Requirements:
* You must have a fully verified and configured Mailchimp account.
* Both the **Transactional API Key** and the **Transactional API Version** must be copy/pasted into the connector settings.

### Use Case - send a transactional email in a flow:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Mailchimp Transactional connector and choose the `Send Transactional Email` capability.
* This Mailchimp capability has four capability level properties that can be filled out 1 of 2 ways:
   * Manually inserting the desired values into the fields.
   * Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* `Subject` is simply the subject of the email being sent.
* `Text` is where the desried, formatted message is inserted.
* `From Email` is used to identify the one sender email address.
* `Recipient Email` is used to identify the recipient email address(es).
   * This capability is able to send one message to either one recipient or multiple.
      * To do this, simply insert a comma-separated list of desired email address.
         * E.g. `customer_1@gmail.com, customer_2@gmail.com, customer_3@gmail.com, customer_4@gmail.com`
            * The connector handles any unintentional spacing oddities with the comma-seperated values.
* The Mailchimp Transactional connector does not generate any output on its own.
   * To see the HTTP response object sent by Mailchimp you can do the following:
      * Add an HTTP block after your Mailchimp connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Mailchimp connector.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

### Use Case - add an email to your allowlist in a flow:
* Add the Mailchimp Transactional connector to the desired flow and choose the `Add Email to Allowlist` capability.
* This Mailchimp capability has two capability level properties that can be filled out 1 of 2 ways:
   * Manually inserting the desired values into the fields.
   * Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* `Allowlist Email` is used to identify the email address being added to the allowlist.
   * Can only handle one email at a time.
* `Comment` is an optional description of why the email was added to the allowlist.
* The Mailchimp Transactional connector does not generate any output on its own.
   * To see the HTTP response object sent by Mailchimp you can do the following:
      * Add an HTTP block after your Mailchimp connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Mailchimp connector.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

### Use Case - print JSON object containing list of account senders in a flow:
* Add the Mailchimp Transactional connector to the desired flow and choose the `List Account Senders` capability.
* This Mailchimp capability has zero capability level properties!
   * Therefore, all you have to do is plug it into the desired position in your flow and click apply.
* The Mailchimp Transactional connector does not generate any output on its own.
   * To see the HTTP response object sent by Mailchimp you can do the following:
      * Add an HTTP block after your Mailchimp connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Mailchimp connector.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

### Use Case - create custom API call:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow then click save.
* Once inside the flow sandbox add the Mailchimp connector and choose the `Make Custom API Call` capability.
* This Mailchimp connector capability has 4 capability level properties that can be manually filled out:
   * **Endpoint**:
      * Used to call a specific operation from inside the Mailchimp Transactional API.
         * E.g. `/messages/send, /allowlist/add, rejects/add, etc.`
            * Visit the [Mailchimp Transactional API documentation](https://mailchimp.com/developer/transactional/api/) for more endpoints.
   * **Method**:    
      * Specifies the HTTP CRUD request.
         * E.g. `GET, POST, PUT, DELETE, PATCH.`
   * **Headers**:    
      * Key-value pairs that represent the meta-data associated with the Mailchimp Transactional API request and response.
         * E.g. ` Content-Type: application/json`
   * **Body**:   
      * Used to manually craft a JSON request body for the Mailchimp Transactional API.
* The Mailchimp connector does not generate any output on its own.
   * To see the information retrieved by the Mailchimp connector you can do the following:
      * Add an HTTP block after your Mailchimp connector.  
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Mailchimp connector.
         * Choose from any of the offered successful response output variables.
            * rawResponse
            * statusCode
            * headers
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

# Capabilities

Leave this section blank: it will be generated automatically

