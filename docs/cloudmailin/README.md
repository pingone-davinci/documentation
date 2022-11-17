# CloudMailin Connector

Author: Terry Sigle <terrysigle@pingidentity.com>

# Introduction

CloudMailin delivers your transactional email with confidence, security and transparency.

## Requirements

To use the connector, you'll need:

- CloudMailin Username
- CloudMailin API Key

## Obtain CloudMailin Account

1. Create or use an existing account with [CloudMailin](https://www.cloudmailin.com/).
2. Create an API Username and Key.

## Setting up the connector

In DaVinci, add a **CloudMailin Connector** connection

### Connector settings

In the connector details page, under the General tab, provide the following attributes and **Apply**.

- CloudMailin Username
- CloudMailin API Key

# Using the connector in a flow

The typical use of this connector is within a flow when an email is to be sent as part of the running the flow. Use cases that this connector implements include:

## Sending an Email

To send an email, add the CloudMailin connector as a node in a flow. Setting the connector variables (email, subject and to) will immediately send the email via the CloudMailin service.

# Capabilities

### Send Plain Text Email (sendPlainEmail)

Send email with a subject and plain text email

#### Email To `textField`

Email Address (seperated by commas) to send To

#### Email Subject `textField`

Subject of the email

#### Plain Text Body `textField`

Plain text body of the email

---
