# CLEAR Connector

**Author:** Matthew Teets

# Introduction

CLEAR is a secure identity verification platform that allows businesses to quickly and accurately verify users. With CLEAR’s hosted ID Verification UI, businesses can enhance user authentication while maintaining the integrity and privacy of sensitive data.

The CLEAR connector for PingOne DaVinci integrates CLEAR’s verification services into your workflows, enabling seamless identity verification processes. This connector supports creating verification sessions and retrieving verification results.

# Setup

## Resources
For information and additional help, see the following sections of the CLEAR Verified documentation:
- [CLEAR Documentation](https://docs.clearme.com/docs/getting-started)
- [API Keys](https://docs.clearme.com/docs/api-keys-1)
- [Web App Verification](https://docs.clearme.com/docs/web-app)
- [Verification Session API](https://docs.clearme.com/reference/api-keys)

## Requirements

To use the CLEAR connector, the following are required:
- A valid API Key for accessing CLEAR’s API.
- A Project ID for the specific CLEAR project you wish to integrate with.

These can be found inside your CLEAR Console.

## Setting up the connector

- Navigate to the CLEAR connector's general configuration in PingOne DaVinci.
- Enter the required credentials:
   - **API Key**: The API key provided by CLEAR.
   - **Project ID**: The ID of the CLEAR project you are integrating with.
- Configure the following properties:
   - **Secure Endpoint Selection**: Choose between the following:
     - `https://verified.clearme.com` (returns non-sensitive PII).
     - `https://secure.verified.clearme.com` (returns sensitive PII).

# Using the connector in a flow

After setting up the CLEAR connector, you can use it in your flows to:

- Redirect users to CLEAR’s hosted UI for verification.
- Retrieve and process user verification results.

## Capabilities

### Redirect to CLEAR

This capability redirects a user to CLEAR's hosted ID verification UI, then redirects them back into the PingOne DaVinci flow.

Output Schema:
```
{
  "id": "string",
  "object_name": "verification_session",
  "authenticated": true,
  "authentication_methods": [
    "string"
  ],
  "activated_authentication_methods": [
    "string"
  ],
  "checks": [
    {
      "name": "string",
      "value": true,
      "status": "completed",
      "additional_details": {
        "watchlist_hits": {
          "hits": [
            {
              "entity_type": "person",
              "details": {
                "name": [
                  "string"
                ],
                "alias": [
                  "string"
                ],
                "country": [
                  "string"
                ],
                "address": [
                  {
                    "line1": "string",
                    "line2": "string",
                    "city": "string",
                    "state": "string",
                    "postal_code": "string",
                    "country": "string"
                  }
                ],
                "date_of_birth": [
                  {
                    "day": 0,
                    "month": 0,
                    "year": 0
                  }
                ],
                "date_of_death": [
                  {
                    "day": 0,
                    "month": 0,
                    "year": 0
                  }
                ],
                "place_of_birth": [
                  "string"
                ],
                "gender": [
                  "string"
                ],
                "nationality": [
                  "string"
                ],
                "position": [
                  "string"
                ],
                "passport_number": [
                  "string"
                ],
                "id_number": [
                  "string"
                ],
                "notes": [
                  "string"
                ],
                "created_at": [
                  {
                    "day": 0,
                    "month": 0,
                    "year": 0
                  }
                ],
                "modified_at": [
                  {
                    "day": 0,
                    "month": 0,
                    "year": 0
                  }
                ],
                "source_urls": [
                  "string"
                ]
              },
              "source_lists": [
                {
                  "name": "string",
                  "summary": "string",
                  "url": "string"
                }
              ],
              "hit_types": [
                "sanction"
              ]
            }
          ],
          "updated_at": 0
        }
      },
      "params": {}
    }
  ],
  "completed_at": 0,
  "created_at": 0,
  "email": "string",
  "expires_at": 0,
  "fields_to_collect": [
    "string"
  ],
  "ip": [
    "string"
  ],
  "phone": "string",
  "redirect_url": "string",
  "status": "success",
  "token": "string",
  "updated_at": 0,
  "user_agent": [
    "string"
  ],
  "user_created": false,
  "user_id": "string",
  "traits": {
    "address": {
      "line1": "string",
      "line2": "string",
      "city": "string",
      "state": "string",
      "postal_code": "string",
      "country": "string"
    },
    "dob": {
      "day": 0,
      "month": 0,
      "year": 0
    },
    "email": "string",
    "first_name": "string",
    "last_name": "string",
    "middle_name": "string",
    "second_family_name": "string",
    "full_last_name": "string",
    "phone": "string",
    "ssn4": "string",
    "ssn9": "string",
    "identification_number": "string",
    "identification_type": "string",
    "document": {
      "nationality": "string",
      "document_type": "drivers_license",
      "issuing_country": "string",
      "document_number": "string",
      "date_of_expiry": {
        "day": 0,
        "month": 0,
        "year": 0
      },
      "gender": "string",
      "date_of_birth": {
        "day": 0,
        "month": 0,
        "year": 0
      },
      "first_name": "string",
      "last_name": "string",
      "middle_name": "string"
    },
    "document_front": "string",
    "document_back": "string",
    "face_scan_preview": "string"
  },
  "project_id": "string",
  "custom_fields": {}
}
```


