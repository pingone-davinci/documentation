# IDmelon Connector

## Doc draft

Author: IDmelon


# Introduction

You can use the IDmelon connector as part of a PingOne DaVinci flow to enhance the user experience with passwordless authentication using a smartphone, employee's badge or access card as security key.


# Setup


## Resources

For information and setup help, see the following sections of the IDmelon documentation:


## https://docs.idmelon.com/docs/for_administrators/simple_signon_and_idp_integration/idmelon-connector-for-pingone-davinci/


## Requirements

To use the connector, you'll need:

 * A PingOne account
* An IDmelon account with administrator access
* Users with security key for the passwordless experience

## Create your IDmelon administration panel

Visit [panel.idmeon.com](https://panel.idmeon.com) to create or access your account. See [Create your administration panel](https://docs.idmelon.com/docs/for_administrators/get_started/create_your_administration_panel/) for the help.


## Setting up the connector

In DaVinci, add an IDmelon connection. For help, see [Adding a connection](https://docs.idmelon.com/docs/for_administrators/simple_signon_and_idp_integration/idmelon-connector-for-pingone-davinci/).



### Connector settings

 **Provider name:** 
Enter a custom name for it.
 
**Auth Type:**
Chose the Oauth2.
 
**Redirect URL:** 
Copy this value, we will use this value in the IDmelon Panel.
 
**Issuer URL:** 
Empty this value as is.
 
**Authorization Endpoint:** 
https://sso.idmelon.com/api/oidc/idp/authorize/
 
**Token Endpoint:**
https://sso.idmelon.com/api/oidc/idp/token/
 
**User Info Endpoint:** 
https://sso.idmelon.com/api/oidc/idp/userinfo/
 
**Client ID:** 
Get this value from the IDmelon Panel
 
**Client Secret:** 
Get this value from the IDmelon Panel



# Using the connector in a flow

See [Adding a connection](https://docs.idmelon.com/docs/for_administrators/simple_signon_and_idp_integration/idmelon-connector-for-pingone-davinci/).

You can use the connector in a variety of use cases, such as:


## [ Smartphone as security key]

See [Smartphone as security key](https://docs.idmelon.com/docs/for_administrators/introduction/idmelon_passwordless_orchestration_platform/offering_managed_security_keys/#smartphone-as-security-key)



## [ Employee badge or access card as security key]

See [Employee badge or access card as security key](https://docs.idmelon.com/docs/for_administrators/introduction/idmelon_passwordless_orchestration_platform/offering_managed_security_keys/#employee-badge-or-access-card-as-security-key)


# Capabilities

Leave this section blank: it will be generated automatically


# Troubleshooting

If you are having issues with the IDmelon connector, you can try the following: 

* Follow the example provided in the Resources guide step by step to ensure that the initial flow works correctly. 
* Contact IDmelon [support](https://idmelon.com/contact-us).



## Common solutions

https://docs.idmelon.com/

## Troubleshooting resources


### [Resource description]

https://docs.idmelon.com/
