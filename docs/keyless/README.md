# Keyless Connector

## Doc draft

Author: Michele Donzelli


# Introduction

The Keyless protocol implements zero-knowledge biometric (ZKB™) authentication and key management enabled by the unique combination of state-of-the-art biometrics with zero-knowledge cryptography and privacy-enhancing multi-party computation. Keyless ZKB™ authentication supports several biometric modalities, including facial recognition and user behavior modeling.

# Setup						
Keyless provides security-enhancing and privacy-preserving passwordless biometric multi-factor authentication to Ping DaVinci using the OpenID Connect (OIDC) authentication standard. Keyless acts as an identity provider (IdP), authenticating users using a strong cryptographic based digital signature that is immutable and tamper-proof.

As part of your onboarding with Keyless, you should have received the items below. If you don't have one or more of the items, please reach out to your primary Keyless contact or to info@keyless.io.					
Click here to get your credentials from the Keyless Delivery team.


## Resources

For information and setup help, see the following sections of the Keyless documentation:


## https://docs.keyless.io/workforce/


## Requirements

To use the connector, you'll need:									
Client ID
Client Secret 
Well-known URI										
Client ID: The Client ID serves as the identification parameter used by the client application for authentication and authorization purposes.


Client Secret: The Client Secret is a confidential value that serves as the identification secret for the client application. It is used in combination with the Client ID to authenticate the client application securely.


Well-Known URI: The Well-Known Page refers to a public URL that provides access to public information related to the system. This includes details such as the Issuer (identity provider) and Endpoints (URLs for various services) that can be utilized by client applications.
									


## Setting up the connector

In DaVinci, create a new Keyless connection and assign it a name. Click on the hamburger menu for a new connection and choose the edit option to access the connection details.

Make note of the Redirect URL to be used in Keyless. The rest of the information will be filled in later after obtaining the required details from Keyless.

If you require a Keyless tenant, it is necessary to request it in advance. The delivery team at Keyless will provide you with the required information mentioned in the documentation, such as the Client ID and Client Secret. Kindly reach out to the Keyless delivery team to obtain these details before proceeding with the steps outlined above.

Please provide the following information to the Keyless Delivery Team:
Sign-in Redirect URIs: the Redirect URL you noted in DaVinci

The Keyless delivery team will provide the following connection information to be used in DaVinci:

Client ID
Client Secret
Well-known Metadata URL


In DaVinci, enter the Client ID and Client Secret you obtained from Keyless.

Copy the following parameters from the metadata URI:

Issuer URL
Authorization Endpoint
Token Endpoint
User Info Endpoint

Go back to DaVinci and add the remaining details that you copied from Keyless: Issuer URL, Authorization Endpoint, Token Endpoint, User Info Endpoint.

If not already present, add openid, email, and profile to the Scope. Enable the option to Send state with request by toggling it on.

Click on Apply to save your settings and complete the creation of the Keyless connector.

### Connector settings

# Using the connector in a flow

## Authenticating users with Keyless

Create a new HTTP connector and choose the HTML Form capability.

Set up the HTML Form node as follows:

Provide a Title, such as "Sign in with Keyless."
In the Fields List section, click on Add.
Enter "preferred_username" as the Property Name.
Enter "Username" as the Display Name.
Click on Apply.

Connect and include the Keyless connector in your workflow.

Configure the Keyless node and add the following details:

In the Query Parameters, add a new parameter.
Enter "login_hint" as the Key.
Click on "{}" and select the "preferred_username" output variable from your HTML Form.
Click on Apply.
