# WinMagic MagicEndpoint Connector

Author: WinMagic

The MagicEndpoint connector allows you to add explicit device and user-based authentication that does not require user action within the PingOne DaVinci flow. 

MagicEndpoint is based on the principle that the endpoint can perform public key-based authentication that no other device or bad actor can duplicate. Leveraging this inherent capability within endpoint devices significantly reduces the attack surface. The breakthrough behind MagicEndpoint's technology means a client only has to authenticate to the endpoint to verify they are in possession of the device, and the endpoint can do the remote authentication on behalf of the user, with no user action required. MagicEndpoint does not need phones or external tokens. Smarter, faster passwordless authentication means no more obtaining codes from mobile devices, or accepting insecure "push" notifications, or re-setting multiple passwords. 

The result? With the MagicEndpoint connector, CIOs and CISOs can be confident their employees and data are protected while reducing and eventually eliminating the need for password support.



## Setup


### Resources

In DaVinci, add a MagicEndpoint connection in the flow when authentication is required.

Configure MagicEndpoint IdP OIDC Service Providers:
* [How to configure MagicEndpoint IdP OIDC Service Providers](https://magicendpoint10-en.knowledgebase.winmagic.com/Configuration/IdP_Configuring_MagicEndpoint_IdP_OIDC.html)

MagicEndpoint IdP:
* [MagicEndpoint Enterprise Authentication](https://magicendpoint10-en.knowledgebase.winmagic.com/index.html)


### Requirements

To use the connector, you’ll need:

1. SecureDoc Enterprise Server and MagicEndpoint IdP installed
2. A MagicEndpoint license
3. MagicEndpoint Windows Client installed on the endpoint 
4. MagicEndpoint Authenticator (for Out of Band Support) on mobile devices (iOS and Android)


### Setting up MagicEndpoint IdP

1. Obtain MagicEndpoint – OIDC URL settings:

Admin can login to MagicEndpoint IdP web portal and obtain OIDC URLs from Configuration -> OIDC 

2. Add Service Provider – PingOne: 
* Admin can add an OIDC service provider by clicking on "+ Add Service Provider" on Configuration -> OIDC
* Service Provider (SP) Name: PingOne
* Client Name: PingOne
* Redirect URL: Obtain from PingOne console
* Client Secret: * Enter a new secret *
* Session exp. (sec): 180
* Claim Type: Email

Note: Make a note of your **Client Name (Client ID)** and **Client Secret**. You will use them in the **Setting up the connector** section.


### Connector settings

* Token Endpoint: *obtain from MagicEndpoint IdP settings*
* User info Endpoint: *obtain from MagicEndpoint IdP settings*
* Client ID: *obtain from MagicEndpoint IdP settings*
* Client Secret: *obtain from MagicEndpoint IdP settings*
* Scope: OpenId

## Install MagicEndpoint IdP server, Client, and Enrolling:

Before adding the connection in DaVinci, ensure MagicEndpoint client is installed and enrolled on endpoints.

1. Installing MagicEndpoint IdP into your SecureDoc Enterprise Server environment:
[Steps to installing MagicEndpoint IdP --SecureDoc Server Environment](https://magicendpoint10-en.knowledgebase.winmagic.com/Configuration/Install_ME_IdP.html)
 
2. Configuring a SecureDoc Profile and Package to deploy MagicEndpoint IdP-based Authentication: 
[Configure a SecureDoc Profile and Package -- IdP-based Authentication ](https://magicendpoint10-en.knowledgebase.winmagic.com/Configuration/Configure_ME_IdP_Profile_Package.html)
 
3. Deploying the MagicEndpoint Client Software to Endpoint Devices:
[Deploy MagicEndpoint Client Software to the Endpoint ](https://magicendpoint10-en.knowledgebase.winmagic.com/Configuration/Deploy_ME_Client.html)
 
4. Configure MagicEndpoint IdP – as a User to enroll Winmagic Authenticator (for Out of Band support)
[How to Configure MagicEndpoint IdP- as a User](https://magicendpoint10-en.knowledgebase.winmagic.com/Configuration/IdP_Configuration_User.html)
[How to Configure MagicEndpoint IdP Mobile Device Functionality](https://magicendpoint10-en.knowledgebase.winmagic.com/Configuration/IdP_Configuring_MagicEndpoint_IdP_Mobile.html)


## Use cases

### [Passwordless Pre-Boot Authentication](https://winmagic.com/en/solutions/passwordless-pre-boot-authentication/)
### [Passwordless Authentication for Windows Login](https://winmagic.com/en/solutions/passwordless-authentication-for-air-gapped-networks/)
### [Passwordless Authentication for Air Gapped Networks](https://winmagic.com/en/solutions/passwordless-authentication-for-air-gapped-networks/)
### [Passwordless Authentication for VPN via RADISU](https://winmagic.com/en/passwordless-authentication-for-vpn-via-radius/)

## About WinMagic
WinMagic is a leading developer of cybersecurity solutions that, over the course of 25 years, has raised the bar for endpoint encryption. As a result, WinMagic is trusted by over 2500 businesses and government agencies and has over 3 million active licenses globally. WinMagic's authentication and encryption products protect your company's data, on-premises or in the cloud. The company's solutions are platform-independent and secure data on devices using Windows, Linux, and Mac systems. WinMagic delivers a seamless authentication and encryption experience that increases productivity while all employees and data are protected. For more information, visit www.winmagic.com
