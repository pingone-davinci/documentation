# Infinipoint Connector

Author: Infinipoint


# Introduction

The Infinipoint DIaaS (Device-Identity-as-a-Service) is a cloud-delivered security platform that protects access to all applications, for any user and device, from anywhere. Infinipoint is designed to be both easy to use and deploy while providing complete device visibility and control. Infinipoint verifies users’ identities paired with deep insights into your users’ devices, Infinipoint gives you the policies and controls you need to limit access based on the device. Users get a consistent login experience with infinipoint’s Single SignOn (SSO) that delivers centralized access to both on-premises and cloud applications. With Infinipoint, you can protect against risky devices, as well as unwanted access to your applications and data. This combination of user and device trust builds a strong foundation for a zero-trust security model.

# Setup

The Infinipoint connector in PingOne DaVinci will perform an OIDC redirect to the Infinipoint service for device authentication and redirect back to PingOne DaVinci to continue the authentication flow.

Use the Infinipoint "Identity Providers" wizard to add a "PingOne DaVinci Connector" and copy the details to the "Infinipoint Connector" configuration in PingOne.

## Resources

For information and setup help, see https://infinipoint.atlassian.net/wiki/spaces/INFPT/overview

# Capabilities

### Redirect to IdP (loginFirstFactor)


OIDC redirect to IDP

#### OIDC Login `button`

#### showPoweredBy `toggleSwitch`

#### skipButtonPress `toggleSwitch`

---
