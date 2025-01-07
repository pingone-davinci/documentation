# Vidos Connector

## Introduction

The Vidos Connector is a powerful tool designed to integrate Vidos' decentralized identity services with PingOne DaVinci's no-code orchestration. This connector helps enterprises to seamlessly incorporate Vidos Verifier and Universal Resolver services into identity management workflows, enabling a broad set of credential use cases. Enhance security and privacy by leveraging decentralized identity and verifiable credentials in your flows while delivering improved user experience.

## Main Use Cases:

- **Verifiable Credential Verification:** Integrate the Vidos Verifier to check with the issuer that the credentials are valid credentials in line with W3C standards and Anoncreds, ensuring that credentials are legitimate and unaltered.
- **Decentralized Identity Resolution:** Use the Vidos Universal Resolver to resolve DIDs across [multiple methods](https://go.vidos.id/did-methods), enabling secure and decentralized identity verification within enterprise systems.
- **Extending PingOne Neo:** Extend the capabilities of PingOne Neo to accept verifiable credentials from Ping Identity and many other issuers from any supported Vidos DID Method.
- **Futureproof Flows with Vidos Services:** The connector is built to support future feature releases, meaning new service capabilities and versions are instantly available in the Vidos Connector.

## Setup

### Resources

For detailed information and assistance with setup, refer to the following sections of the Vidos documentation:

- [Getting Started with Vidos Universal Resolver](https://go.vidos.id/ping-get-started-with-the-universal-resolver)
- [Using the Vidos Verifier](https://go.vidos.id/ping-using-the-vidos-verifier)

### Requirements

To use the Vidos Connector, you'll need:

- **Ping Identity DaVinci Account:** A valid account with access to DaVinci's flow creation and management features.
- **Vidos API Access:** API keys with permissions for accessing the Vidos Universal Resolver or Verifier services. You can create an account [here](https://dashboard.vidos.id/register) for free. Learn more about [IAM configuration](https://go.vidos.id/ping-iam-configuration).
- **Basic Knowledge of DIDs and VCs:** Familiarity with decentralized identifiers and verifiable credentials is recommended.

### Step 1: Preparing for Integration in DaVinci

Before adding the Vidos Connector in DaVinci, ensure the following prerequisites are met:

1. **Obtain Vidos API Credentials:**
    - Log in to your Vidos account.
    - Navigate to the API keys section and generate a new key for use with the Universal Resolver and/or Verifier services.
    - Enable the appropriate policies to ensure the API key is authorized to access the resolver or verifier services.
    - (Optional) You can add or edit inline permissions to configure additional permissions to be able resolve and verify.
    - Save the API key securely. This will be needed during the Connector configuration.
2. **Set Up Your Vidos Services:**
    - Ensure that you have configured the resolver and/or verifier services you intend to use in the Vidos dashboard.
    - Obtain the verifier and/or resolver instance endpoints. These will be needed in your flows.

### Step 2: Adding the Vidos Connector in DaVinci

Follow these steps to integrate the Vidos Connector in DaVinci:

1. **Log in to DaVinci:** Access your [DaVinci dashboard](https://console.pingone.com/davinci/index.html).
2. **Navigate to the Connectors Section:** Go to the ["Connectors" tab](https://console.pingone.com/davinci/index.html#/connections).
3. **Add the Vidos Connector:**
   - Click "Add Connector" and search for "Vidos" or locate the Vidos Connector in the Service Connectors section.
   - Click to view the Connector capabilities and add it to you Connectors.
   - Accept the default name or rename the connection as required, then click Create.
   - The Vidos Connector should now be visible in your Connectors list.
4. **Review the Vidos Connector:** Go to the "Connectors" tab and search for "Vidos".

## Configuring the connector

In DaVinci, after adding the Vidos Connector, you’ll need to configure it by setting the following parameters:

### Configuring the Vidos Connector in DaVinci

Follow these steps to configure the Vidos Connector in DaVinci:

1. **Log in to DaVinci:** Access your [DaVinci dashboard](https://console.pingone.com/davinci/index.html).
2. **Navigate to the Connectors Section:** Go to the ["Connectors" tab](https://console.pingone.com/davinci/index.html#/connections) and search for "Vidos". Note: If you have not yet added the connector, see Setup instructions above.
3. **Configure General Settings:**
   - Vidos API Key: Enter your Vidos API Key obtained from [Vidos](https://dashboard.vidos.id/iam/api-keys) with appropriate resolver or verifier permissions.
   - Verifier Version: Select the verifier version to use when verifying credentials and presentations, or accept default.
4. **Apply Your Settings:** Click Apply to save your settings.
   You can now add the Connector in a flow to verify credentials and presentations or resolve DIDs.

### Connector Setting Details

The following settings are configurable in the Connector Settings:

- Vidos API Key: The Vidos API Key can be obtained from [Vidos](https://dashboard.vidos.id/iam/api-keys). It should have appropriate resolver or verifier permissions.
- Verifier Version: Select the verifier version to use when verifying credentials and presentations, or accept default.
  Note: The Vidos Connector can be configured to use Vidos Resolver and Verifier services individually or together. You can also configure multiple instances of the Connector to use different configurations or instance endpoints, or to separate functionality.

## Using the connector in a flow

Once the Vidos Connector is configured, it can be used in various identity management flows within DaVinci:

### Vidos Resolver: Decentralized Identifier Resolution

To integrate the Universal Resolver, for example, to verify the authenticity of a user’s DID during the login process, follow these steps:

1. Add the Vidos Connector to your flow.
2. Select the connector to edit the configuration.
3. Select the capability to use in your flow: “Universal Resolver - Resolve DID" capability as the action.
4. Configure the following fields, preferably using global or flow variables obtained in your flow:
   - **Resolver Instance URL:** This field should contain a Vidos Resolver endpoint value (e.g. `https://<resolver-name>.resolver.service.<region>.vidos.id`) for an instance that the API Key has permission to access. The instance permissions and configuration policies and can be managed via the Vidos Dashboard. It is recommended to obtain this value from a Global or Flow Instance Variable.
   - **Decentralized Identifier:** This field should contain a DID in the format `did:<did-method>:<method-specific-id>` (e.g. `did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK`.
5. Apply the configuration to the connector.
6. The connector outputs can be used in subsequent connectors in your flow.
   The key output fields are:
   - **success** (boolean): Indicates if the resolution was successful
   - **output** (object): Contains the resolver response
     - **rawResponse** (object): The DID resolution result
       - **didResolutionMetadata**: Resolution metadata including content type and query details
       - **didDocument**: The resolved DID document containing identity information (null if resolution fails)
       - **didDocumentMetadata**: Additional metadata about the DID document
     - **statusCode** (number): HTTP status code (e.g., 200 for success)
     - **headers** (object): Response headers
   - **error** (object): Present when resolution fails
     - **code** (string): Error code (e.g., "resolverInstanceResponseError")
     - **message** (string): Human-readable error description
     - **details** (array): Detailed error information including raw response
     - **httpResponseCode** (number): HTTP error code

#### Example Successful Response

The success field will be true and didDocument will contain the resolved identity information:

```json
{
  "success": true,
  "output": {
    "rawResponse": {
      "didDocument": {
        "id": "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK",
        "verificationMethod": [...],
        "service": [...]
      }
    },
    "statusCode": 200
  }
}
```

More examples of the Universal Resolver can be found at [PingOne DaVinci Connector Use Cases](https://go.vidos.id/ping-connector-use-cases)

### Vidos Verifier: Verifiable Credentials

To integrate the Vidos Verifier to validate verifiable credentials, follow these steps:

1. Add the Vidos Connector to your flow.
2. Select the connector to edit the configuration.
3. Select the capability "Verifier - Verify Credential" as the action.
4. Configure the following fields, preferably using global or flow variables obtained in your flow:
   - **Verifier Endpoint** This field should contain a Vidos Verifier endpoint value (e.g., `https://<verifier-name>.verifier.service.<region>.vidos.id`) for an instance that the API Key has permission to access. The instance permissions and configuration policies can be managed via the Vidos Dashboard. It is recommended to obtain this value from a Global or Flow Instance Variable.
   - **Verifiable Credential:** This field should contain a verifiable credential object (usually passed in from a flow variable or input value), conforming to the W3C Verifiable Credentials Data Model.
   - **Fields**: These are additional options to send to the Vidos Verifier API, for example:
     - Key: `returnCredential`
     - Value: `true`
       See [Vidos Verifier API docs](https://go.vidos.id/docs-api-verifier) for more information.
5. Apply the configuration to the connector.
6. The connector outputs can be used in subsequent connectors in your flow.
   The key output fields are:
   - **success** (boolean): Indicates if verification was successful
   - **output** (object):
     - **results** (array): Detailed check results
     - **checks** (array): List of verification checks performed
     - **statusCode** (number | null): HTTP status code
   - **error** (object): Present when verification fails
     - **code** (string): Error code
     - **message** (string): Error description
     - **httpResponseCode** (number): HTTP error code
    
### Vidos Verifier: Verifiable Presentations

To integrate the Vidos Verifier to validate verifiable credentials, follow these steps:

1. Add the Vidos Connector to your flow.
2. Select the connector to edit the configuration.
3. Select the capability "Verifier - Verify Presentation" as the action.
4. Configure the following fields, preferably using global or flow variables obtained in your flow:
   - **Verifier Endpoint** This field should contain a Vidos Verifier endpoint value (e.g., `https://<verifier-name>.verifier.service.<region>.vidos.id`) for an instance that the API Key has permission to access. The instance permissions and configuration policies can be managed via the Vidos Dashboard. It is recommended to obtain this value from a Global or Flow Instance Variable.
   - **Verifiable Presentation:** This field should contain a verifiable presentation object (usually passed in from a flow variable or input value), conforming to the W3C Verifiable Credentials Data Model.
   - **Fields**: These are additional options to send to the Vidos Verifier API, for example:
     - Key: `returnPresentation`
     - Value: `true`
   - Other available options include
     - challenge (optional): A unique string to prevent replay attacks.
     - **domain** (optional): The domain to scope the verification to.
       See [Vidos Verifier API docs](https://go.vidos.id/docs-api-verifier) for more information.
5. Apply the configuration to the connector.
6. The connector outputs can be used in subsequent connectors in your flow.
   The key output fields are:
   - **success** (boolean): Indicates if verification was successful
   - **output** (object):
     - **results** (array): Detailed check results
     - **checks** (array): List of verification checks performed
     - **statusCode** (number | null): HTTP status code
   - **error** (object): Present when verification fails
     - **code** (string): Error code
     - **message** (string): Error description
     - **httpResponseCode** (number): HTTP error code
   - **Options**:
   - **challenge** (optional): A unique string to prevent replay attacks.
   - **domain** (optional): The domain to scope the verification to.
     5.Apply the configuration to the connector.
     6.The connector outputs can be used in subsequent connectors in your flow.
    
### Additional Information

**Documentation Links**:

- [Vidos Universal Resolver Documentation](https://go.vidos.id/universal-resolver-docs)
- [Vidos Verifier API Documentation](https://go.vidos.id/docs-api-verifier)
  **Support**:
- For any issues or questions, contact [Vidos Support](https://support.vidos.id).
  This integration ensures seamless handling of decentralized identifiers and verifiable credentials within Ping Identity DaVinci, offering robust security and interoperability with W3C standards.

---

## Capabilities

Leave this section blank: it will be generated automatically

## Testing capabilities

You can test each capability of the Vidos Connector individually by running test flows within DaVinci. Use sample DIDs, verifiable credentials or presentations to verify that each action (e.g., Resolve DID, Verify Credential, Verify Presentation) functions correctly.

Here are examples that can be pasted into the code editor view of the fields in the Vidos Connector to test your flow:
**DID Method**

```plaintext
did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK
```

Expected response for the DID method above:

```json
{
  "didDocument": {
    "@context": "https://w3id.org/did-resolution/v1",
    "didResolutionMetadata": {
      "contentType": "application/did+ld+json",
      "query": {
        "did": "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK",
        "method": "key",
        "id": "z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK",
        "didUrl": "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK"
      }
    },
    "didDocument": {
      "id": "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK",
      "verificationMethod": [
        {
          "id": "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK#z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK",
          "type": "JsonWebKey2020",
          "controller": "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK",
          "publicKeyJwk": {
            "crv": "Ed25519",
            "kty": "OKP",
            "x": "Lm_M42cB3HkUiODQsXRcweM6TByfzEHGO9ND274JcOY"
          }
        }
      ],
      "authentication": [
        "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK#z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK"
      ],
      "assertionMethod": [
        "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK#z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK"
      ],
      "capabilityInvocation": [
        "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK#z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK"
      ],
      "capabilityDelegation": [
        "did:key:z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK#z6MkhaXgBZDvotDkL5257faiztiGiC2QtKLGpbnnEGta2doK"
      ],
      "@context": [
        "https://www.w3.org/ns/did/v1",
        "https://w3id.org/security/suites/jws-2020/v1"
      ]
    },
    "didDocumentMetadata": {}
  }
}
```

**Verifiable Credential**

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://w3id.org/security/suites/ed25519-2020/v1",
    "https://w3id.org/security/data-integrity/v2"
  ],
  "credentialSubject": "did:key:z6MkhTNL7i2etLerDK8Acz5t528giE5KA4p75T6ka1E1D74r",
  "id": "urn:uuid:758311b4-61a2-4620-b491-147eda764c1c",
  "issuer": "did:key:zDnaeRpdr3KkQ1NtBhLAWFp76epvaU1spZzGH7AvKtY9KqjZr",
  "proof": {
    "created": "2024-06-03T16:13:45Z",
    "cryptosuite": "ecdsa-jcs-2019",
    "proofPurpose": "assertionMethod",
    "proofValue": "z5Auc6t3vbPbtLKW1esS4Btp98RGJGDd4bDRYzwBgekYDcAye3zyvzgaFS5b3Q2MyYW5A3dwmks6gFLGB67SnQz1M",
    "type": "DataIntegrityProof",
    "verificationMethod": "did:key:zDnaeRpdr3KkQ1NtBhLAWFp76epvaU1spZzGH7AvKtY9KqjZr#zDnaeRpdr3KkQ1NtBhLAWFp76epvaU1spZzGH7AvKtY9KqjZr"
  },
  "type": "VerifiableCredential"
}
```

Expected response for the credential above:

```json
{
  "checks": ["credentialStatus", "format", "notAfter", "notBefore", "proof"],
  "warnings": [
    "tag:missing-required-field-Optional field '/issuanceDate' missing",
    "tag:missing-required-field-Optional field '/expirationDate' missing"
  ],
  "errors": []
}
```

**Verifiable Presentation**

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://w3id.org/security/data-integrity/v2"
  ],
  "type": ["VerifiablePresentation"],
  "verifiableCredential": [
    {
      "@context": [
        "https://www.w3.org/2018/credentials/v1",
        {
          "AlumniCredential": "https://schema.org#AlumniCredential",
          "alumniOf": "https://schema.org#alumniOf"
        },
        "https://w3id.org/security/data-integrity/v2"
      ],
      "id": "http://example.edu/credentials/1872",
      "type": ["VerifiableCredential", "AlumniCredential"],
      "issuer": "did:key:zDnaekGZTbQBerwcehBSXLqAg6s55hVEBms1zFy89VHXtJSa9",
      "issuanceDate": "2010-01-01T19:23:24Z",
      "credentialSubject": {
        "id": "https://example.edu/students/alice",
        "alumniOf": "Example University"
      },
      "proof": {
        "type": "DataIntegrityProof",
        "created": "2023-03-01T21:29:24Z",
        "verificationMethod": "did:key:zDnaekGZTbQBerwcehBSXLqAg6s55hVEBms1zFy89VHXtJSa9#zDnaekGZTbQBerwcehBSXLqAg6s55hVEBms1zFy89VHXtJSa9",
        "cryptosuite": "ecdsa-rdfc-2019",
        "proofPurpose": "assertionMethod",
        "proofValue": "zNqtAbEWenMxFDB8omdCSzY5S1GGNAQjWibDycCnJMkHeLF5apDje6QxSgqsjn5AMqDRkX7dsh9BnVpbAnnkzTX1"
      }
    }
  ],
  "id": "id:test",
  "proof": {
    "type": "DataIntegrityProof",
    "created": "2023-03-01T21:29:24Z",
    "verificationMethod": "did:key:zDnaekGZTbQBerwcehBSXLqAg6s55hVEBms1zFy89VHXtJSa9#zDnaekGZTbQBerwcehBSXLqAg6s55hVEBms1zFy89VHXtJSa9",
    "cryptosuite": "ecdsa-rdfc-2019",
    "proofPurpose": "assertionMethod",
    "proofValue": "zkhFb45dDtvpxfu21fyAMxi4tqRnNKDSouckj24JG9AAKKa2wpoq9RUvACP6kmJmZUrjrP4GVvRLyFJQNhRDCgfS"
  }
}
```

Expected response for the presentation above:

```json
{
  "checks": ["format", "proof"],
  "warnings": [],
  "errors": []
}
```

## Limitations

- **Service Availability:** The Vidos Connector support Vidos Resolver and Verifier services.
- **Region-Specific Configurations:** Ensure that the selected region in the connector settings correspond with your organizational data compliance requirements.

# Troubleshooting

Please see [PingOne DaVinci Vidos Connector Troubleshooting](https://go.vidos.id/pingone-davinci-connector-troubleshooting) for common issues and steps to resolve them.
