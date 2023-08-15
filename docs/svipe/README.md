# Svipe Connector

Author: Svipe

# Introduction
You can use the Svipe Connector to create applications with strong authentication, which will improve security by verifying identities of users’ ID credentials from biometric id-documents issued by 145+ countries.

The SvipeID app has to be downloaded on the user's device in order to use the connector.
The user has to go through the fast onboarding process.

Svipe Connector can be used for:
Strong authentication
Identity Verification
Sharing verified information
Additional factor

Svipe issues all identity credentials as JWT and W3C-compliant verified credential identity claims. 
# Setup
## Resources
For information and setup help, see the following sections of the Svipe documentation:
Svipe developer portal (https://developer.svipe.com/home)
Svipe documentation (https://developer.svipe.com/documentation#/why-svipe)
Creating Svipe application (http://developer.svipe.com/applications)
Davinci documentation:
Connecting DaVinci with PingOne
Importing a flow from the Flow Library
Adding a connector
 ## Requirements
To use the connector, you'll need:
A PingOne environment with a production instance of DaVinci
A Svipe application, for test purposes this can be created on the Svipe developer page (http://developer.svipe.com/applications). For commercial use, you need to reach out to sales@svipe.com to sign a contract.

## Setting up the connector
In DaVinci, add a Svipe connection. For help, see Adding a connector.
## Connector settings
Client ID
The Client ID of the application you created in the Svipe developer portal.
Client Secret
The Client Secret of the application you created in the Svipe developer portal.
Other settings that can be gathered in the Svipe Developer portal:
Authorization Endpoint
Userinfo Endpoint
Token Endpoint
Issuer URL

# Using the connector in a flow
You can use the connector in a variety of use cases, such as:
Identity Verification:
	Verify the identity of your users with SvipeID app downloaded on their phones
	For help, see the verification flow  
	(https://developer.svipe.com/documentation#/verification)
Asking for claims 
Ask for particular information of your users, such as: full name, face, phone, email
For help, see the claims documentation (https://developer.svipe.com/documentation#/README?id=oidc-scopes-and-claims)
Verifiable credentials 
	Svipe has taken a step forward by incorporating support for the emerging standard of verifiable credentials (VC). We issue all our identity credentials as W3C-compliant identity claims
Authentication
Additional factor


