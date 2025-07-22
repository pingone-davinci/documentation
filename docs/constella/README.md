# Constella Connector

# Introduction

Constella provides breach intelligence and account takeover detection using the world’s largest data lake of compromised credentials and infostealer data. It enables businesses to assess risk signals associated with email addresses and passwords.

The Constella connector for PingOne DaVinci integrates Constella’s risk evaluation services into your workflows, allowing you to detect exposed or high-risk identities early in the authentication process. This connector supports evaluating email risk scores and detecting account takeover risk based on known credential exposure.

# Setup

## Resources

For more details about the Constella APIs, reach out to a Constella representative for access to developer documentation and credentials.
- [Constella Intelligence](https://constella.ai/)

## Requirements

To use the Constella connector, the following are required:
* **Base URL** for your Constella tenant (including `https://`)
* **X-AppToken** for service authorization
* **X-Token** and **X-Username** for user identification and authentication

These credentials will be provided by Constella.

## Setting up the connector

* Navigate to the Constella connector's general configuration in PingOne DaVinci.
* Enter the required credentials:
  * **Base URL**: The base API URL provided by Constella (e.g., `https://api.constellaintelligence.com`).
  * **X-AppToken**: Application token for accessing Constella services.
  * **X-Token**: Token identifying the authenticated user.
  * **X-Username**: Hexadecimal identifier for the authenticated user.
* Configure the following input properties as needed for your flow:
  * **Email Address**: The email to be evaluated.
  * **Hashed Password** *(for ATO use case)*: The plaintext password used to calculate account takeover risk.
  * **Profile** *(for Email Risk use case)*: Indicates the nature of the email identity being evaluated (e.g., `ExposedIdentity`).

# Using the connector in a flow

After setting up the Constella connector, you can use it in your flows to:

* Evaluate the risk score of an email address based on known exposure and profile classification.
* Check whether an email and password pair exists in known breach records to assess account takeover risk.

## Capabilities

### Evaluate Email Risk

This capability checks if the given email address is found in any known breaches and returns a risk score. You can optionally specify a **profile** to fine-tune the evaluation:

* `FakeIdentity`
* `ExposedIdentity` (default)
* `MalIdentity`

Output Schema:
```
{
  "rawResponse": {
    "status": 200,
    "description": "OK",
    "data": {
      "score": 95,
      "rating": "VERY HIGH",
      "webmailer": false,
      "anon_webmailer": true,
      "breaches_count": 98,
      "unique_combo_count": 2,
      "malicious_count": 0,
      "legit_count": 0,
      "first_seen": "2020-01-11",
      "last_seen": "2025-07-17"
    }
  },
  "statusCode": 200,
  "headers": {
    "access-control-allow-origin": "*",
    "content-type": "application/json",
    "date": "Tue, 22 Jul 2025 18:27:21 GMT",
    "server": "Apache",
    "status": "200 OK",
    "vary": "Accept-Encoding",
    "x-version": "1.16.0",
    "content-length": "189",
    "connection": "keep-alive"
  }
}
```

---

### Detect Account Takeover Risk

This capability hashes the given email address and password, then checks against Constella’s breach records to determine if the combination appears in exposed credentials.

Output Schema:
```
{
  "rawResponse": {
    "status": 200,
    "description": "OK",
    "data": {
      "results": [
        {
          "hashed_value": "973dfe463ec85785f5f95af5ba3906eedb2d931c24e69824a89ea65dba4e813b",
          "hashed_password": "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08",
          "password_encryption_method": [
            "sha-256"
          ],
          "password_clear": 1
        }
      ],
      "query": {
        "pagination": {
          "total": 1,
          "count": 1,
          "page": 0
        }
      },
      "next_id": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiIiLCJhdWQiOiIiLCJpYXQiOjE0NDg2MTUyMzUsIm5iZiI6MTQ0ODYxNTIzNSwiZGF0YSI6eyJwYWdpbmF0aW9uUGFyYW1ldGVycyI6eyJhdG9WMlwvc2VhcmNoIjp7ImZyb21fcGFnZSI6MCwiZnJvbV9pZCI6MCwiZnJvbV9vZmZzZXQiOjF9fX19.RM6x6JJoAlkFxc7CZbBFkGEZSP5q9sKvcDxdF_TJu3M"
    }
  },
  "statusCode": 200,
  "headers": {
    "access-control-allow-origin": "*",
    "content-type": "application/json",
    "date": "Tue, 22 Jul 2025 18:27:42 GMT",
    "server": "Apache",
    "status": "200 OK",
    "vary": "Accept-Encoding",
    "x-version": "1.16.0",
    "content-length": "480",
    "connection": "keep-alive"
  }
}
```


