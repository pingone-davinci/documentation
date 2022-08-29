# Hellō Connector


# Introduction

Hellō allows you to offer all the choices your users may want to log in with only one connector. Hellō will gather all the claims you request including verified email, verified phone, and profile picture.  

# Setup

The Hellō connector in PingOne DaVinci will perform an OIDC redirect to the user's Hellō Wallet, and then redirect back to PingOne DaVinci.

1. Create and configure your app using the Hellō Console ([console.hello.dev](https://console.hello.dev)). You can add your logo(s), privacy policy, and terms of service later if you want.

1. Copy the client id from the Hellō console to the connector 

1. Create and copy the client secret from the Hellō console to the connector 

1. Copy the redirect uri from the connector to the Hellō console.

1. Add other claims you want by adding the corresponding scopes in addition to `openid` eg. `openid name email picture`. See [Hellō Claims](https://www.hello.dev/documentation/hello-claims.html#current-scopes) for a full list.

Setup should now be complete!

## Resources

[Hellō Documention](https://www.hello.dev/documentation/#introduction)
[Hellō Claims](https://www.hello.dev/documentation/hello-claims.html#current-scopes)
[Hellō Console](https://console.hello.dev))

# Capabilities

### Redirect to Hellō (loginFirstFactor)


Redirect to Hellō

#### OIDC Login `button`

#### showPoweredBy `toggleSwitch`

#### skipButtonPress `toggleSwitch`

---
