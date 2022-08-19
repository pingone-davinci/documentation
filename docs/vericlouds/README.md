# VeriClouds Connector

Author: Stan Bounev (stanb@vericlouds.com)

# Introduction
Use the VeriClouds connector to interact with any DaVinci flow.

The VeriClouds connector has capabilities that can be tied together to improve your company's security posture and detect logins compromised credentials to your systems. 

You can use the connector to check for compromised credentials during the following situations:
 - New account creation
 - Sign-on authentication
 - Password reset

# Setup

- Subscribe for a VeriClouds account and obtain an API key for your subscription
- In DaVinci, add a VeriClouds Compromised Credentials connection.
- Configure connector settings
    - apiKey - provided by VeriClouds
    - apiSecret - provided by VeriClouds

## Pre-Requisites
 - VeriClouds subscription

## Resources
For information and setup help, see the following sections of the documentation: [Documentation Example](https://docs.pingidentity.com/bundle/davinci-pingone-connector/page/hlh1642792860912.html) Ask Pingidentity Davinci Support to provide you necessary information on how to make Setup Flow via Davinci Admin Panel.

# Capabilities

### Check Compromised (checkCompromised)


Check if an username, email or phone number has a compromised password

#### identifierType `dropDown` `required`


The type of identifier. The Vericlouds connector currently accepts email, username, or phone_number.


 - email
 - username
 - phone_number

#### Identifier `textField`


The user's identifier value (email, username, or phone number)

#### Password `textField`


User's Password

---



## Troubleshooting
If you are having issues, you can try the following:
 - Ensure VeriClouds API key saved
 - Ensure VeriClouds subscription has not expired
 - For each connector in the flow, make sure that all of the mandatory inputs have been provided
 - Use the Analytics feature to see where the flow stopped

## Common solutions 
 - You may want to identify some compromised credential examples on your domain in order to be able to fully test out the implementation

## Troubleshooting resources
[VeriClouds API documentation](https://www.vericlouds.com)

 
