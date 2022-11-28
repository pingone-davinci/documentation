# tru.ID Connector

Author: Luis Pedrosa

# Introduction

tru.ID is a SIM-based possession factor verification platform. Use tru.ID to register users, verify transactions, manage access and login, or whenever you need to build extra trust in mobile numbers. Leveraging the SIM-based authentication infrastructure of mobile networks, tru.ID provides, in real time, proof of mobile digital presence and possession of a mobile digital identity.

SIM-based authentication is a superior form of MFA because it is cryptographically secure, phishing-resistant, and compliant with regulations for strong customer authentication and device binding. tru.ID aims to make universal adoption of MFA easier by removing security theatre from authentication journeys while providing stronger, simpler account security. The platform is live in 20 countries covering 2bn+ mobile subscribers, so you integrate once and scale globally.

# Setup

## Resources

For information and setup help, please see the following sections:

* [tru.ID developer documentation](https://developer.tru.id/docs/integrations/pingid)
* [OIDC bridge setup documentation](https://github.com/tru-ID/oidc-bridge/blob/main/integration-pingID/README.md)

## Requirements

To use the connector, you'll need:

* tru.ID developer account ([sign up](https://tru.id/signup))
* OIDC Bridge application to control the verification flow ([more info](https://github.com/tru-ID/oidc-bridge))
* PingID DaVinci tenant


## Setting up the connector in DaVinci

In Davinci, add a tru.ID connection via the "Connections" tab in your Davinci Environment. 

### Configuring the connector

Fill in the following connector fields:

* Issuer - tru.ID issuer url e.g. https://eu.api.tru.id/
* Authorization Endpoint - tru.ID authorization endpoint url e.g. https://eu.api.tru.id/oauth2/v1/auth
* Token Endpoint - tru.ID token endpoint url e.g. https://eu.api.tru.id/oauth2/v1/token
* JWKS URI - tru.ID JWKS url e.g. https://eu.api.tru.id/oidc/.well-known/jwks.json
* Client ID - your OIDC-enabled project client ID
* Client Secret - your OIDC-enabled project client Secret
* Scope - fill it in with `openid`

# Using the connector in a flow

The tru.ID connector allows you to verify the phone number of a pingID user. You can use it in a variety of use cases:

* As an MFA step, after you have identified the user through user/pass, external SSO, etc.
* As a passwordless authentication method, where the user logs in using their mobile device

## MFA step

When a user tries to login using a DaVinci Flow, you can trigger an MFA step through
tru.ID after the initial identification method (e.g. username/password, SSO, etc.)

Since you have access to the user's profile after the initial identification step, if
the profile contains a phone number attribute you can use it as a verification factor.

## Passwordless authentication

If one of your user's profile is associated with a valid phone number, then they can use that device to perform passwordless authentication.

In this use case, the first authentication factor is the tru.ID connector.

# Capabilities

### Authenticate (initializeAuthorizationRequest)




#### Username `textField`


The username of the authenticating user.

#### State `textField`


State bypass to make this work

#### tru.ID OIDC `button`

#### showPoweredBy `toggleSwitch`

#### skipButtonPress `toggleSwitch`

---



# Troubleshooting

If you have any questions you can contact us at https://support.tru.id/

# Limitations

Users in your user directory must have a valid phone number associated with their
profile, in order to use the capabilities of this connector

