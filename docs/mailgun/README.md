# Mailgun Connector

Author: Matthew Teets

# Introduction

The Mailgun connector allows users to send emails, configure mailing lists, and retrieve domain event statistics within a flow.

### Capabilities:

##### Message Capabilities:

- `Send Message`

##### Mailing List Capabilities:

- `Create Mailing List`
- `View Mailing List`
- `Update Mailing List`
- `Delete Mailing List`

##### Mailing List Member Capabilities:

- `Create Mailing List Member`
- `View Mailing List Member`
- `Update Mailing List Member`
- `Delete Mailing List Member`

##### Statistic Capabilities:

- `Domain Stats`

##### Custom Capability:

- `Make Custom API Call`

# Setup

## Resources

#### For information and additional help, see the following sections of the Mailgun API documentation:

Mailgun Capabilities API Documentation:

- [Mailgun API Reference](https://documentation.mailgun.com/en/latest/api_reference.html)

Message Capabilities:

- [Send Message](https://documentation.mailgun.com/en/latest/api-sending.html#sending)

Mailing List Capabilities:

- [Create Mailing List](https://documentation.mailgun.com/en/latest/api-mailinglists.html#mailing-lists:~:text=POST%20/lists-,Creates,-a%20new%20mailing)
- [View Mailing List](https://documentation.mailgun.com/en/latest/api-mailinglists.html#mailing-lists:~:text=/%3Caddress%3E-,Returns,-a%20single%20mailing)
- [Update Mailing List](https://documentation.mailgun.com/en/latest/api-mailinglists.html#mailing-lists:~:text=PUT%20/lists/%3Caddress%3E-,Update,-mailing%20list%20properties)
- [Delete Mailing List](https://documentation.mailgun.com/en/latest/api-mailinglists.html#mailing-lists:~:text=DELETE%20/lists/%3Caddress%3E-,Deletes,-a%20mailing%20list)

Mailing List Member Capabilities:

- [Create Contact](https://documentation.mailgun.com/en/latest/api-mailinglists.html#mailing-lists:~:text=lists/%3Caddress%3E/members-,Adds,-a%20member%20to)
- [View Contact](https://documentation.mailgun.com/en/latest/api-mailinglists.html#mailing-lists:~:text=address%3E/members/%3Cmember_address%3E-,Retrieves,-a%20mailing%20list)
- [Update Contact](https://documentation.mailgun.com/en/latest/api-mailinglists.html#mailing-lists:~:text=address%3E/members/%3Cmember_address%3E-,Updates,-a%20mailing%20list)
- [Delete Contact](https://documentation.mailgun.com/en/latest/api-mailinglists.html#mailing-lists:~:text=address%3E/members/%3Cmember_address%3E-,Delete,-a%20mailing%20list)

Statistics Capabilities:

- [Domain Stats](https://documentation.mailgun.com/en/latest/api-stats.html#stats:~:text=domain%3E/stats/total-,Returns,-total%20stats%20for)

DaVinci Documentation:

- [Login to DaVinci](https://portal.singularkey.com/dashboard)
- [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
- [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)

## Requirements

#### To use the Mailgun connector:

- You must have access to the Mailgun dashboard.
  - Sign up for an account [here](https://signup.mailgun.com/new/signup)
- You must have a valid API key in order to make any calls to the Mailgun API.
  - Find your Mailgun API key [here](https://app.mailgun.com/app/account/security/api_keys)
    - The API key is also called the <b> Private API Key.

## Setting up the connector

#### Mailgun Connector General Settings:

- Navigate to the Mailgun connector via the _**Connections**_ tab in DaVinci.
- Select _**New Connection**_ in the upper right-hand corner.
- Search for the desired connector (in this case, Mailgun).
- Select the Mailgun connector.
- Once the Mailgun connector has been added the _**Your Connections**_ list, click on the connector.
- From here you will see three text fields labeled **Domain**, **API Key**, and **API Version**.
  - **Domain**:
    - This text field is for your custom Mailgun domain.
      - E.g. `DOMAIN_NAME.mailgun.org`
      - To create/verify your own custom domain follow the steps provided [here](https://help.mailgun.com/hc/en-us/articles/203637190-How-Do-I-Add-or-Delete-a-Domain-)
  - **Mailgun API Key**:
    - Before pasting your API key into the text field you must first base64 encode the key with 'api'
      - E.g. `echo -n 'api:qnbxdMY444lF2gwM3fDx'| base64` = `YXBpOnFuYnhkTVk0NDRsRjJnd00zZkR4`
        - The above command is for the Mac Terminal
    - Copy and paste your base64 encoded API Key into the text field.
  - **Mailgun API Version**:
    - This field will already be filled out.
      - Only change this if the API version is out of date.
  - `Click Apply`

# Using the connector in a flow

### Some Mailgun connector use cases:

- Send a message with multiple recipients from a flow.
- Creating a new member inside of a specified mailing list.
- Retrieve all mailing statistics for a specified event and time frame.
- Create a custom API Call to Mailgun.

### Mailgun API Request Requirements:

- You must have a fully functioning and configured Mailgun account and control panel.
- Your Domain must be fully verified with Mailgun.
- You must have a base64 encoded API key
  - This API key will be ≈ 36 bytes long
- The **Domain**, **Mailgun API Key**, and **Mailgun API Version** text fields must be filled in the connector settings.

---

### Simple Use Case - send a message with multiple recipients from a flow:

- Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
- Select `Blank Flow`.
- Insert the desired name and description and click `Create`.
- Once inside the flow sandbox add the Mailgun connector and select the `Send Message` capability.
- This Mailgun capability has eight capability level properties that can be filled out 1 of 2 ways:
  1.  Manually inserting the desired values into the respective text fields.
  2.  Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      - E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
- **Capability Level Properties:**
  1. `Sender Name` is simply the name of the sender.
  2. `From Address` is the email address of the sender.
     - This email address must contain the verified mailgun domain, e.g. `davinci@YOUR_DOMAIN.mailgun.com`
  3. `To Address` is the email address of the recipient(s).
     - This can contain multiple email addresses.
     - If multiple emails are used each email must be separated by a comma.
  4. `Subject` is the subject if the message being sent.
  5. `Message` is the text body of the message.
  6. `Tag` is a user-defined outgoing message identifier.
     - **This property is optional**
  7. `BCC` same as `To` but with typical bcc functionality.
     - This can contain multiple email addresses.
     - If multiple emails are used each email must be separated by a comma.
     - **This property is optional**
  8. `CC` same as `To` but with typical cc functionality.
     - This can contain multiple email addresses.
     - If multiple emails are used each email must be separated by a comma.
     - **This property is optional**
- Click `Apply`
- The Mailgun connector does not generate any output on its own.
  - To see the HTTP response object returned by the Mailgun API you can do the following:
    - Attach an HTTP block after your Mailgun connector.
    - Click on the Custom HTML Message capability.
    - In the _**Message**_ text area select the circular angel bracket button ( **{}** )
      - From the dropdown, select the Mailgun connector option with the `Send Message` capability listed.
      - Choose the `output (object)` by clicking `(+)`.
    - Click `Apply`
- In the upper right hand corner click Save, Deploy, and Run.

---

### Simple Use Case - creating a new member inside of a specified mailing list.:

- Add the Mailgun connector to the desired flow and select the `Create Mailing List Member` capability.
- This Mailgun capability has six capability level properties that can be filled out 1 of 2 ways:
  1.  Manually inserting the desired values into the respective text fields.
  2.  Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      - E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
- **Capability Level Properties:**
  1.  `Mailing List Address` is the email address for the desired mailing list.
  2.  `Member Address` is the valid email address for the new member being added.
  3.  `Member Name` is the name of the new member.
      - **This property is optional**
  4.  `Member Attributes` is a set of arbitrary attributes that can be assigned to the new member.
      | Key|Value|
      |---|---|
      | age| 21|
      | gender| male|
      | company| Ping Identity|
      - **This property is optional**
  5.  `Member Subscription Status` is used to set the member as subscribed or unsubscribed by typing **yes** or **no**.
      - If left blank the default is **yes**.
  6.  `Member Upsert Permissions` if set to **yes** it allows updating/inserting new info if the member being added already
      exists. If set to **no** it raises a duplication error.
      - If left blank the default is **no**.
- Click `Apply`
- The Mailgun connector does not generate any output on its own.
  - To see the HTTP response object returned by the Mailgun API you can do the following:
    - Add an HTTP block after your Mailgun connector.
    - Click on the Custom HTML Message capability.
    - In the _**Message**_ text area select the circular angel bracket button ( **{}** )
      - From the dropdown, select the Mailgun connector option with the `Create Mailing List Member` capability listed.
      - Choose the `output (object)` by clicking `(+)`.
    - Click `Apply`
- In the upper right hand corner click Save, Deploy, and Run.

---

### Use Case - create custom API call:

- Add the Mailgun connector to the desired flow and select the `Make Custom API Call` capability.
- This Mailgun capability has 5 capability level properties that can be filled out 1 of 2 ways:
  1.  Manually inserting the desired values into the respective text fields.
  2.  Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      - E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
- **Capability Level Properties:**
  1.  **Endpoint**:
      - Used to call a specific operation from inside the Mailgun API.
        - E.g. `/lists, /DOMAIN/stats, /DOMAIN/messages, etc.`
          - Visit the [Mailgun API Documentation](https://documentation.mailgun.com/en/latest/api_reference.html) for more endpoints.
  2.  **Method**:
      - Specifies the HTTP CRUD request.
        - E.g. `GET, POST, PUT, DELETE, PATCH.`
  3.  **Query Parameters**:
      - The key-value pairs that appear after the question mark in the URL.
        - E.g. `event=delivered&duration=1h`, `address=mailing.list@domain.com`, `address=customer@email.com`, etc...
      - **This property is optional if not required**
  4.  **Headers**:
      - Key-value pairs that represent the meta-data associated with the Mailgun API request and response.
        - E.g. ` Content-Type: application/json`
      - **This property is optional if not required**
  5.  **Body**:
      - Used to manually craft the raw JSON request body for the Mailgun API.
      - **This property is optional if not required**
- The Mailgun connector does not generate any output on its own.
  - To see the information retrieved by the Mailgun connector you can do the following:
    - Add an HTTP block after your Mailgun connector.
    - Click on the Custom HTML Message capability.
    - In the _**Message**_ text area select the circular angel bracket button ( **{}** )
      - From the dropdown, select the Mailgun connector.
      - Choose from any of the offered successful response output variables.
        - rawResponse
        - statusCode
        - headers
    - `Click apply`
- In the upper right hand corner click Save, Deploy, and Run.

---

# Capabilities

Leave this section blank: it will be generated automatically
