# HUMAN Connector

Author: HUMAN Security


# Introduction

You can use the HUMAN Security Connector to enable PingOne DaVinci to detect and take action when an end user attempts to create or log in to an account using a compromised credential. Through this integration, a PingOne Davinci administrator can ensure all credentials being used have not been previously compromised using HUMAN Credential Intelligence.

This connector allows you to analyze if the credentials are compromised to safeguard accounts during account login, account creation, and password update. For any of the above flows, we recommend the following actions in case the credentials are compromised: forcing a password reset, requesting a different password on account creation, or password update. This flag can also be used to conditionally initiate an MFA step. This way, the account is not vulnerable to credential-stuffing attacks or to attackers gaining unauthorized access using compromised credentials. 


# Setup

Setting up the connector
In DaVinci, add the HUMAN connector. You can do this in DaVinci by navigating to the Connectors tab on the side menu > select Add Connector > Search for HUMAN > Add. 

Connector settings
HUMAN Authentication Token
The token used for authorization with the HUMAN backend.
HUMAN App ID
The HUMAN Security application id.

Both configuration items can be retrieved from the HUMAN Security console. Please contact HUMAN Security for more details.

# Using the connector in a flow

You can use the HUMAN Security connector to validate whether the credentials entered are flagged as compromised or not, and then act upon the result.

To use the HUMAN Security connector:

Add the connector to your flow by using the Add Connector button.
Connect the left side of the connector to the submit action of your login form.
Connect the right side of the connector to both a successful login connector (All Triggers True) and whatever action you would like to take in case the credentials are flagged as compromised, for example, a password reset form (All Triggers False).
Click on the HUMAN Security Connector, click Configure, and add the HUMAN Security Auth Token and Application Id.

You can use the connector in a variety of use cases, such as:

# Capabilities

Check for Compromised Credential
* Checks username and password for a compromised credential.
  * Username (required)
  * Password (required)
 
These will be sourced from a user input form earlier within the flow. Select the {} brackets in the respective fields on the HUMAN connector capability configuration and choose the input form this should pull from. You can then select the approriate username and password field that will be sent through each field to check against the HUMAN API for a compromised credential.


