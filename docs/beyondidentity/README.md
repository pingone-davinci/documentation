# Beyond Identity Connector


Author: Suresh Bhandarkar


# Introduction

Beyond Identity is fundamentally changing how the world logs in with a groundbreaking invisible, un-phishable MFA platform that provides the most secure and frictionless authentication on the planet. We stop ransomware and account takeover attacks in their tracks and dramatically improve the user experience. Beyond Identity’s state-of-the-art platform eliminates passwords and other phishable factors, enabling organizations to confidently validate users’ identities. The solution ensures users log in from authorized devices, and that the device meets the security policy requirements during login and continuously after that. Our revolutionary approach empowers zero trust by cryptographically binding the user’s identity to their device and analyzing hundreds of risk signals on an ongoing basis. The company’s advanced risk policy engine enables organizations to implement foundationally secure authentication and utilize risk signals for protection, rather than just for detection and response. For more information on why Intuit, Snowflake, and Roblox use Beyond Identity, please visit www.beyondidentity.com.


# Setup

The Beyond Identity connector in PingOne DaVinci will perform an OIDC redirect to the Beyond Identity service for passwordless authentication and redirect back to PingOne DaVinci to continue the authentication flow. 

Use the following URLs to configure the Beyond Identity Connector in PingOne DaVinci.

- Issuer: https://auth.byndid.com/v2
- Authorization: https://auth.byndid.com/v2/authorize
- Token: https://auth.byndid.com/v2/token
- Userinfo: https://auth.byndid.com/v2/userinfo
- JWKS: https://auth.byndid.com/v2/.well-known/jwks.json
- Scope: OpenID
- Client ID: You will receive this from Beyond Identity.
- Client Secret: You will receive this from Beyond Identity.

## Resources

For information and setup help, see https://support.beyondidentity.com




