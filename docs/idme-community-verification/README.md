
# ID.me Community Verification Connector

Author: Ryan Friess


# Introduction

The ID.me Community Verification solution allows organizations to easily define pre-configured community verification policies to verify users community affiliation at the exact level of trust required to access a requested service or receive a discount for a product or service.

The ID.me solution orchestrates multiple verification methods at each level of trust to ensure that all of your users are able to easily and securely prove their community affiliation online. Military members, Teachers, First Responders, Nurses - we have got you covered.


# Prerequisites
1. Before you begin, sign up for an ID.me Developer Account. [Sign up for free!](https://developers.id.me)
2. Reach out to the ID.me Sales Engineer team: [partnersupport@id.me](mailto:partnersupport@id.me)

# Setup

## Set Up Your ID.me Developer Account
1. Proceed to Start a New Integration and click Continue
2. Input organization information and click Continue
3. Once an organization is created, you can proceed to View My Applications
4. Click Create New
5. Input application information. Please note, Only application name, display name, and redirect URI are required fields
6. Enter your PingOne Davinci Redirect URI (you can find this on the ID.me Connector setting page)
7. Once all fields are input and formatted correctly, you may proceed to create your ID.me application by clicking Continue

## Configure PingOne Davinci Connector
1. Enter Connection Name
2. Enter your ID.me Client ID
3. Enter your ID.me Client Secret
4. Under scopes, select the checkbox for openid (openid is mandatory)
5. Select your desired community verification policy


# ID.me Pre-Verified Network

Once users verify their community affiliation with ID.me with any of our partners in our network, they will not be be prompted to verify again unless their credentials expire. These users will still have to accept the permissions to share their user attributes your app has requested. To enforce community verification, please reach out to [partnersupport@id.me](mailto:partnersupport@id.me).


# Troubleshooting resources

Email ID.me at [partnersupport@id.me](mailto:partnersupport@id.me) for any issues with your ID.me's PingOne Davinci integration.


# Resources

Please visit [ID.me's Developer Site](https://developers.id.me/documentation/groups) to learn more about ID.me's Community Verification Solution.
