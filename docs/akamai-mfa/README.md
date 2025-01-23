# Akamai MFA Connector


Author: Subhrajyoti Das (Akamai)


# Introduction


The Akamai MFA connector lets you use Akamai Multi-Factor Authentication in your PingOne DaVinci flow.

Akamai Multi-Factor Authentication​ (MFA) is a workforce multifactor authentication service that strengthens organizations' security postures by providing strong secondary authentication to cloud, on-premises, web-based, SaaS, and IaaS applications—in addition to the existing primary authentication, such as the identity provider (IdP) system.
​Akamai MFA​ leverages FIDO2 standards enabling users to authenticate securely to protected resources with the ​Akamai MFA​ mobile app that transforms existing smartphones into phone security keys.
It also empowers users by offering them a frictionless authentication process with the familiar experience of push notifications and many other secondary authentication methods.

# Setup
For information and setup help, see the following documentation:
* Akamai MFA Documentation:
  * [Getting started with Akamai MFA](https://techdocs.akamai.com/mfa/docs/set-up-mfa)
    
  * [Configure and manage Akamai MFA​](https://techdocs.akamai.com/mfa/docs/manage-mfa)
    
  * [Set up an OIDC integration](https://techdocs.akamai.com/mfa/docs/oidc-integration)
    
  * [Enroll devices](https://techdocs.akamai.com/mfa/docs/self-enroll-mfa) and [authenticate](https://techdocs.akamai.com/mfa/docs/auth-mfa) using ​Akamai MFA​

DaVinci documentation:

  * [PingOne DaVinci Documentation](https://docs.pingidentity.com/davinci/davinci_landing_page.html)


## Requirements

To use the connector, you'll need:

* An Akamai Control Center account with Akamai MFA enabled and configured

* An OIDC integration set up in Akamai MFA

* Akamai user account to use for testing


## Set up your Akamai MFA OIDC integration

1. In Akamai Control Center, add an OIDC integration. For help, see OIDC integration in the Akamai MFA documentation.
2. Enter a name for your integration.
3. In Algorithm, select HS256.
4. Click Save and Deploy.

Note your **Integration ID**, **Client Secret**, and **Signing Key**. You’ll use these credentials in the connector configuration. 


## Setting up the connector

In DaVinci, add an Akamai MFA connection under the Connectors tab > “+ Add Connector” > Search for “Akamai MFA”. Once the connector has been added to your connector library, you can search for it in the Search bar and click on it to begin configuring per the below steps.


### Connector settings

To configure the connector, you will need:

* Redirect URL: This is required to be configured on the Akamai side and allows the app to redirect back to PingOne DaVinci after authentication completes

* Auth Endpoint: Gathered from Akamai Akamai well-known endpoint

* Token Endpoint: Gathered from Akamai Akamai well-known endpoint

* Integration ID: Generated from app set up on Akamai side

* Client Secret: Generated from app set up on Akamai side

* Signing Key: Generated from app set up on Akamai side

* Scope: Defaults “openid”

# Use Case

## Workforce MFA

​Akamai Multi-Factor Authentication​ (MFA) is a workforce multifactor authentication service that strengthens organizations' security postures by providing strong secondary authentication to cloud, on-premises, web-based, SaaS, and IaaS applications—in addition to the existing primary authentication, such as the identity provider (IdP) system.

# Troubleshooting

If you run into issues with the connector configuration, please reach out to your Akamai support representative for assistance.

## Troubleshooting resources


### Akamai MFA Tech Docs

Please review the Akamai MFA Tech Docs page listed [here](https://techdocs.akamai.com/mfa/docs/welcome-mfa) for any additional troubleshooting.

You can review additional information on DaVinci [here](https://docs.pingidentity.com/davinci/davinci_landing_page.html)


