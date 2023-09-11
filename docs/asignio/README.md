# Asignio Connector

## Doc draft

Author: Asignio, Inc.


# Introduction


Asignio replaces vulnerable passwords with handwriting biometrics in the browser, using letters, numbers, and symbols drawn on a touch screen to uniquely authenticate the user. In just a few seconds, synchronous biometric analysis proves user presence, reduces fraud, and provides best-in-class security. 

Asignio's multiple web-based biometrics allow for easy authentication on any touch-device, while eliminating the need for passwords and one-time passcodes.

Asignio handwriting-based biometrics can be enabled for Ping users in a few easy steps:

# Setup


## Resources

For information and setup help, see the following sections of the Asignio documentation:


### [Asignio OIDC Documentation](https://partner.asignio.com/Documentation/OIDCDocumentation)


## Requirements

To use the connector, you'll need:

* Asignio tenant
* Asignio administrator account with Asignio Sign
* Asignio [Partner Administration](https://partner.asignio.com) site access
* Registered OIDC resource

## Asignio tenant

Provide company details to request a trial Asignio tenant. These should include: 


Company name 
Administrator email address 

This information can be sent to info@asignio.com, or relayed directly to your Asignio Account Executive. 

## Asignio administrator account

Your new Asignio tenant can be configured via a self-service Partner Administration portal. The portal site itself is protected by Asignio biometrics, and thus it is necessary for a tenant administrator to enroll an Asignio Sign to proceed with configuration. 
 
[Create an Asignio Sign](https://my.asignio.com/AccountCreation/Invite) using the previously provided administrator email address. Activation code will be included with the Asignio trial response. 

## Asignio Partner Administration site

Your new Asignio tenant can be managed via https://partner.asignio.com. This portal will be used in the next step to connect to Ping. 


You can also add other administrators or invite users to enroll in Asignio biometrics on this site.  

## Register OIDC resource

Register a resource (OIDC) on the [Asignio Partner Admin site](https://partner.asignio.com) corresponding to the DaVinci connection.

1. Login to *https://partner.asignio.com* with your newly enrolled administrator Asignio account.
2. Select **Resources**
3. Select **+** to add a new resource 
Enter the following configuration 
4. Fill out the following fields and select **save**:

| Field                 | Value to Provide                     |
| --------------------- | ------------------------------------ |
| App Name              | *Choose a name for DaVinci connector instance* |
| Redirect URI          | *Copy & paste Redirect URL from DaVinci Asignio connector* |
| API Integration       | `OIDC`                               |
| Client Authentication | `none`                 |
| Advanced Settings > Use PKCE | `false`                 |

*Certain security features may not be fully supported at this time; please contact your Ping & Asignio account executives if your use case necessitates a different configuration from the above.*

## Setting up the connector

In DaVinci, add an Asignio connection. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector settings

After opening the Asignio connection from the **Connections** page in DaVinci, complete each of the following fields in the **General** tab:


| Field                 | Value to Provide                     |
| --------------------- | ------------------------------------ |
| Issuer URL              | *`https://authorization.asignio.com`* |
| Authorization Endpoint  | *`https://authorization.asignio.com/authorize`* |
| Token Endpoint  | *`https://authorization.asignio.com/token`* |
| User Info Endpoint  | *`https://authorization.asignio.com/userinfo`* |
| Client ID | *Copy & paste the Client ID of the resource you created on [Asignio Partner](https://partner.asignio.com) in the previous step.*                 |
| Client Secret | *On [Asignio Partner](https://partner.asignio.com), click* ***Generate****, and copy & paste client secret directly to DaVinci.*                 |
| Scope | *`openid profile email`*                 |


# Using the connector in a flow

Asignio biometrics authenticate a user enrolled with a given email address based on handwriting recognition ± facial verification.

You can use the connector in a variety of use cases, such as:

* Multi-factor authentication step
* Passwordless biometric authentication
* Biometric identity verification


## Multi-factor authentication step

Successful authentication from OIDC can be used to supplement existing authentication checks with a biometric assertion. Add handwriting recognition & other biometric checks to authenticate users. 


## Passwordless biometric authentication

Replace passwords and/or one-time passcodes with biometrics.

Asignio's handwriting recognition & other biometric checks can be used in lieu of vulnerable passwords to authenticate users via OIDC.


## Biometric identity verification

If Asignio is configured to require identity verification, users are required to initially present an identity document which is subsequently bound to handwriting & facial biometrics. 

Users who complete Asignio authentication re-assert the original possession of the ID. 

The claims returned by exchanging the OIDC `access_token` contain details on verified identity status of the user.


# Capabilities

Leave this section blank: it will be generated automatically


## Troubleshooting resources

### Asignio Support

If you have any questions, email **support@asignio.com**, or visit **[asignio.com](https://www.web.asignio.com/contact)**.


### Testing capabilities

You can test each capability individually. For help, see [Testing capabilities](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).
