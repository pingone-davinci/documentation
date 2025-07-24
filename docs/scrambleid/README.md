# ScrambleID Connector

# Introduction

The ScrambleID connector for PingOne DaVinci allows you to initiate and complete OIDC authentication flows with ScrambleID from within a DaVinci journey. This connector supports redirect-based login using a configured client ID and client secret, and it returns validated identity tokens and user claims to your flow.

# Setup

## Resources

For more details about OIDC configuration and credentials, contact a ScrambleID representative.
- [ScrambleID](https://scrambleid.com)

## Requirements

To use the ScrambleID connector, you must have:
* A valid **Client ID** and **Client Secret** registered with ScrambleID.
* The following configuration URLs from ScrambleID:
  * **Discovery Document URL**
  * **Authorization Endpoint**
  * **Token Endpoint**
  * **Scope**

You must also register the **DaVinci Redirect URI** with ScrambleID so that token responses can be properly returned to PingOne.

## Setting up the connector

* Navigate to the ScrambleID connector's general configuration in PingOne DaVinci.
* Enter the required credentials:
  * **Discovery Document URL**: The well-known endpoint for your applicaiton
    * (e.g., `https://demo.scrambleid.com/oidc/ping/.well-known/openid-configuration`).
  * **Authorization Endpoint**: OIDC authorization endpoint.
  * **Token Endpoint**: OIDC token endpoint.
  * **Client ID**: Provided by ScrambleID.
  * **Client Secret**: Provided by ScrambleID.
* Optionally configure:
  * **Scope**: Defaults to `openid offline_access`
  * **Send State with Request**: Toggle to include a unique state value in each request.
  * **Application URL**: The post-authentication redirect URL to your app (if using an embedded DaVinci widget).

# Using the connector in a flow

After setting up the ScrambleID connector, you can use it in your flows to:

* Redirect the user to ScrambleID for login
* Automatically handle the token exchange
* Receive identity attributes (like email, name, and username)

## Capabilities

### Redirect to ScrambleID

This capability initiates an OIDC login request to ScrambleID and returns tokens and identity claims once the user successfully authenticates.

Output Schema:
```
{
  "sub": "test@example.com",
  "email": "test@example.com",
  "first_name": "John",
  "last_name": "Smith",
  "username": "test@example.com",
  "at_hash": "vpc5bIBbN8lodalowFMxpg",
  "aud": "c445b9b0-5654-4e35-a536-3bea064a0383",
  "exp": 1753381282,
  "iat": 1753377682,
  "iss": "https://demo.scrambleid.com",
  "tokens": {
    "access_token": "PWPLkh9-oTuiwWgZT3nREQZ5KLvEUxWiPhcljCnZpC0",
    "expires_at": 1753381282,
    "id_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IjU5YThkM2IyZmVmMjdjMjQifQ.eyJzdWIiOiJtYXR0aGV3dGVldHNAcGluZ2lkZW50aXR5LmNvbSIsImVtYWlsIjoibWF0dGhld3RlZXRzQHBpbmdpZGVudGl0eS5jb20iLCJmaXJzdF9uYW1lIjoiTWF0dGhldyIsImxhc3RfbmFtZSI6IlRlZXRzIiwidXNlcm5hbWUiOiJtYXR0aGV3dGVldHNAcGluZ2lkZW50aXR5LmNvbSIsImF0X2hhc2giOiJ2cGM1YklCYk44bG9kYWxvd0ZNeHBnIiwiYXVkIjoiYzQ0NWI5YjAtNTY1NC00ZTM1LWE1MzYtM2JlYTA2NGEwMzgzIiwiZXhwIjoxNzUzMzgxMjgyLCJpYXQiOjE3NTMzNzc2ODIsImlzcyI6Imh0dHBzOi8vZGVtby5zY3JhbWJsZWlkLmNvbSJ9.RlELpwW3e_Gx57JhUCOhraV5vghNVSFSa8GF3t0FpDH8I--KAK16d8XIwYcW9sRH355VkeAD3pDPIoQRJA3v0l5pkDK3A62qkS8BXD545Rnh9Fii6-3oSDeBMwZcedrUEm-XICqADKTxzPCEaJ-wtGFCumJgAROsxALmxNWUPyag4joheS11HBk-WiFOLeCAD8PRnPnEdpTiS5HKsrNrwtttH2WmY2-GJg68yQzSetvPEYyXs0iEcHFE7XVnLp43eemWKhRrZ6xIgcl_2ejNU-2N7IoSBAKtn7sgcXDi4xvxh1UqISoX-mogprhvsa1YrEkbAIBDjzQkB8mmp_YMHw",
    "scope": "openid",
    "token_type": "Bearer"
  },
  "connectionId": "133d4bfb24b9182a2c452095f1655ea0",
  "connectorId": "scrambleIdConnector"
}
```


