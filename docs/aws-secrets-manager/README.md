# Amazon Secrets Manager Connector

Author: Patrick Cowland (patrickcowland@pingidentity.com) 

# Introduction

[Amazon Secrets Manager](https://aws.amazon.com/secrets-manager/) is a cloud infrastructure service offered by Amazon Web Services (AWS) that allows you to store, manage and rotate API keys, client ID/client secret combinations and other secrets from a central location.

The AWS Secrets Manager connector for DaVinci allows you to externalize system-level secrets outside of the DaVinci flow configuration, simplifying the ongoing rotation of API keys, client secrets and more when used in combination with other connectors, such as when specifiying API connection credentials in the DaVinci HTTP connector's `Make REST API Call` capability.

Using the AWS Secrets Manager connector, you can also ensure no hard-coded credentials are exported alongside core flow logic.

# Setup

## Resources

For information and setup help, see the following sections of the AWS documentation:

* AWS Secrets Manager
    * [Getting Started with AWS Secrets Manager](https://aws.amazon.com/secrets-manager/getting-started/)
    * [Secrets Manager Console](https://console.aws.amazon.com/secretsmanager)
    * [AWS Secrets Manager User Guide](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html)
    * [Managing access keys for IAM users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html)
    * [Attaching A Permissions Policy to Access Secrets](https://docs.aws.amazon.com/secretsmanager/latest/userguide/auth-and-access.html#auth-and-access_secrets)

## Requirements

To use the connector, you'll need:

* An Amazon AWS Account with permissions to access the Secrets Manager Console
* An AWS IAM user access key and secret for API access: 'Access Key ID' and 'Secret Access Key'
* The AWS region code you expect to store secrets in (e.g. eu-west-1)
* A suitable Permissions Policy in AWS to allow the AWS IAM user access key the ability to read, and optionally create/update/delete the secrets in the secrets manager.

## Setting up the connector

In PingOne DaVinci, add a **AWS Secrets Manager** connection. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings

Once you've added the connection click on its logo, or click the "***"  button and "Edit".

You will see the connector's details pop-up. On the GENERAL tab, enter in your

1) AWS Access Key
2) AWS Access Secret
3) AWS Region

Click apply to finish. This ensures that whenever you use this connector in a flow you will not have to reenter enter this information.


# Using the connector in a flow

You can use the AWS Secrets Manager connector to inject external secrets into flow variables for use in further node configuration, or otherwise perform basic management of secrets from within a DaVinci flow template.

Once configured, simply add the AWS Secrets Manager into the flow and choose the desired capability.  The following are example use cases:

## Fetching Secrets for use in the "Make REST API Call" Capability of the HTTP Connector

Unless using a public/unauthenticated API endpoint, the "Make REST API Call" capability of the HTTP Connector requires you to configure API authorization/authentication details into the headers or query/body parameters.  This may include an API Key, a Username/Password for HTTP basic authentication or a client ID/client secret combination.

While these can be stored as sensitive variables in DaVinci, you may want to externalize and centralize such secrets and apply a rotation strategy without having to periodically change variable or flow data in DaVinci.

The "Get Secret" capability of the AWS Secrets Manager DaVinci connector allows you to reference an external secret for the REST API call, without having to handle or manage the secret yourself.

The resulting data object will contain a "secret" response attribute that can be parsed into the relevant data type (e.g. a string parsed to JSON) and used as a parameter in later nodes.  The "response" response attribute contains the full response from the AWS Secrets Manager, including the secret's stored metadata.

If the secret is a binary secret, the connector will base64 encode the secret first.

Simply add the AWS Secrets Manager node before the HTTP node and use the "secret" output variable of the AWS Secrets Manager in the "Make REST API Call" parameters.

## Creating, Updating and Deleting a Secret

The connector offers basic functionality for creating, updating and deleting secrets.  These capabilities can be used for automation purposes, such as  defining or receiving secrets set from other sources, and storing them in AWS for processes outside of DaVinci to use.

The connector supports storing secrets using a custom KMS Key and can optionally overwrite a secret value if a secret with the configured name already exists.

If, when creating a secret, the secret has been previously deleted but is recoverable, the connector also supports optionally recovering the secret before setting the new value.

Deleting the secret will mark the secret for deletion in AWS, but will remain recoverable for 30 days.

# Capabilities


# Troubleshooting

If you have issues with the AWS Secrets Manager connector, you can check the following:

* Verify the connection details are correct, and the secrets are stored in the correct AWS region.
* Verify the AWS IAM User has the appropriate permissions policy applied for the actions used in the flow.
* Alternatively, verify the AWS Secrets themselves have the appropriate permissions policy set for the actions used in the flow.
* For each connector in the flow, make sure that all of the mandatory inputs have been provided.
* Use the Analytics feature to see where the flow stopped.
* Select the Options icon, and turn on Show Node ID. This will make it easier to identify the source of inputs and outputs.

# Limitations

This connector has limited capabilities compared to the full extent of the Amazon Secrets Manager SDK.

Limitations include:
* Managing secret rotation and rotation policy
* Creating binary secrets
* Secret versioning
* Tags for created secrets
* Regional replication of created secrets
* Deleting secrets without a recovery period, or setting a custom recovery period

If you'd like to see more capabilities added or have other suggestions, please let your Ping contact know.

