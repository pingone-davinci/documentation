## Arkose Connector

Author: Arkose Labs


# Introduction

Use the Arkose DaVinci Connector to plugin the Arkose Detect and/or Challenge in any of your identity flows. The Arkose connector offers an easy way to verify the validity of the Arkose token and leverage the intel provided by Arkose to enhance the security of your workflow. The connector response can be used to:
  - Provide session risk information for appropriate authenticaiton decisions i.e. allow/ challenge or deny a session
  - Secure your reset password flow
  - Prevent bulk fake account creations in your user store

and for many similar use cases.


# Setup


## Resources

For information and setup help, see the following sections of the Arkose Labs documentation:


[Calling the Verify API](https://developer.arkoselabs.com/docs/server-side-instructions-v4#calling-the-verify-api)


## Requirements

To use the connector, you'll need:

* [Your Arkose Private Key]
* [Your company URL, if applicable]

Please contact your account team, if you don't have these already.

## Setting up the connector

In the DaVinci platform, add an **Arkose* connection. For help, see [Adding a connection](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html).


### Connector settings

Once you have added the **Arkose** connection, select the connector in the flow studio and edit the connection to update the **General** settings.


#### Company
Provide your company name as it appears on your Arkose Verify URL subdomain

#### Private Key
Provide your Arkose private key for this flow here

# Capabilities

## Verify

This capability is used verify the Arkose token and optionally send log data to Arkose

### Properties

#### Private Key
The Arkose token will be mapped from the previous HTML connection. The value can be mapped as {{local.<connectionID>.payload.output.arkoseToken}} where connectionID is the identifier of the HTML connection that presents the login form to the user in the DaVinci flow.

#### HTTP Method
Use the GET HTTP method to fetch the Verify API response for the current session or POST method to provide optional log data to Arkose Labs, while fetching the API response. The log data is a freeform string that allows information to be passed to the Verify API. This can be used to pass basic information that you want stored by Arkose with the session data. This can be used internally by Arkose when performing manual traffic analysis.

# Connector Response

The connector returns a status code and a raw response object when successful. The fields values from the response object can be individually mapped to downstream connectors to drive the user flows.

# Using the connector in a flow

You can use the connector in a variety of use cases. The connector will require the Arkose session token as an input. The session token will be generated client side upon interaction with the user, for instance, on a login page. 

In order to generate the the Arkose session token, you can use the HTTP connection as follows:
  1. Add the HTTP connection and choose the **Custom HTML Template** Action from the list.
  2. Add the 'username pasword form' under the HTML template. You can choose 'data-skcomponent' class to use the default Ping DaVinci form components.
  3. Add a hidden div tag to the HTML template. This div tag will include the primary form submit button, which is hidden to prevent default form submit. This tag will also include the Arkose token data component.
  4. The HTML template will include an additional submit button (not hidden) which will be used to trigger the Arkose enforcement challenge.
  5. Use the Script template to embed the Arkose javacript on the login form. The script will also override the form's default submit action. 
  6. A callback will be defined to setup and initiate the Arkose session and challenge. Once the challenge is completed, the Arkose session token value will be set in the hidden data component and the form will be submitted to proceed to the next step. For more details on setting up the callback function, please refer to [Arkose Client Side Setup](https://developer.arkoselabs.com/docs/standard-setup#client-side-setup)


Some example use cases are as follows:

## Authenticating a user

The Arkose session token that is generated as part of user credentials submission is verified by the Arkose connector. The connector response can be used in the authentication flow to make authentication decisions and allow/ challenge or deny a user access based on the Arkose risk category for a given session.

## Registering a user

The Arkose session token that is generated as part of user sign up process is verified by the Arkose connector. The connector response can be used in the registration flow to allow/ challenge or deny a user account creation based on the Arkose risk risk category for a given session.

## Resetting a user's password

The Arkose session token that is generated as part of password reset process is verified by the Arkose connector. The connector response can be used in the password reset flow to allow/ challenge or deny a user account creation based on the Arkose risk risk category for a given session.


# Capabilities

### Verify (verify)


This capability is used verify the Arkose token and optionally send log data to Arkose

#### Session Token `textField`


The Arkose session token that is generated on the HTML form (client side setup)

#### HTTP Method `dropDown`


HTTP Method to be used to verify Arkose session


 - GET
 - POST

#### Log Data `textField`


Information to be passed to Arkose along with session data to be used for manual traffic analysis

---

# Troubleshooting

If the connector returns a 400 - bad request as a response, ensure that the Arkose token is correctly mapped as an input to the connector.
