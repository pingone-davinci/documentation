# Incode Connector

Author: Karl Persson


# Introduction


The Incode connector enables you to add Incode’s AI-powered Identity Verification and Authentication into your PingOne DaVinci flows and connect verified real-world identity to Ping Identity user profiles.
 
Incode’s Identity Platform provides fully automated ML-driven document authentication, passive liveness, face recognition matching, and face authentication that can easily and seamlessly be integrated with PingOne DaVinci using OpenID Connect (OIDC).
For example, you can configure Incode to secure your New User Registration or Account Recovery by ensuring that each user’s real-world identity is verified as part of the process.
Once a user’s real-world identity has been Verified by Incode, you can enable face authentication to seamlessly confirm the user’s real-world identity.

# Setup


## Resources

For information and setup help, see the following sections of the Incode documentation:
*[Key Concepts & Definitions](https://developer.incode.com/docs/key-concepts)
*[Create a Standard Workflow](https://developer.incode.com/docs/create-a-standard-workflow)
*[OpenID Connect Configuration](https://developer.incode.com/docs/open-id-connect-oidc)



## Requirements

To use the connector, you'll need:
 
1. 	An account with Incode (please contact support@incode.com)
2. 	At least one workflow setup within the Incode platform (see [here](https://developer.incode.com/docs/create-a-standard-workflow))
3. 	An OIDC configuration within the Incode platform (see [here](https://developer.incode.com/docs/open-id-connect-oidc))

## Setting up the connector

In DaVinci, add an Incode connection. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings

* App ID - The Client ID from the Incode OIDC Client Configuration
* Client Secret - Client Secret from the Incode OIDC Client Configuration
* Issuer URL - Issuer URL for Incode’s Authorization Server provided to you by Incode
* Scope - List of space separated scopes (must be exactly those that were configured in the Incode OIDC Client Configuration)



# Using the connector in a flow

You can use the connector in a variety of use cases, such as:
* User Registration
* Account Recovery
* Password Resets
* Conditional step-up as an additional authentication factor
To include verification of a user’s real-world identity using Incode, you must first enroll, or onboard, the user onto Incode’s platform and create an identity. This is ideally done as part of a New User Registration flow in DaVinci when the user’s Ping Identity user profile is first created. 
Once an Identity exists in Incode’s platform you can configure biometric Face Authentication for any DaVinci flow where validating the real-world identity of a user is required. 
More information on how to set up OIDC configurations within Incode’s platform can be found here[https://developer.incode.com/docs/open-id-connect-oidc].


## Common solutions

* Ensure that the Redirect URI in the Incode OIDC client configuration matches the Redirect URI within the Incode Ping Davinci connector configuration
* Confirm with your Incode support representative that your account has been provisioned in the correct environment that matches the Issuer URL within the Incode Ping Davinci connector configuration
* Ensure that the OIDC scopes configured in the connector and in the Incode OIDC Client Configuration match)
## Troubleshooting resources

Email support@incode.com for any troubleshooting assistance.
