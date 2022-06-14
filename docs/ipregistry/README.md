# ipregistry.co Connector

Author: Mike Simon

# Introduction

The ipregistry connector provides geolocation and threat data and information associated with an IPv4 or IPv6 IP address. The connector interfaces with the ipregistry API to return up to 82 unique data points, including location data, connection data, Autonomous System Number (ASN), company name, domain, carrier data, time zone, currency, and security assessment data. Refer to [API Respone Fields](https://ipregistry.co/docs/fields#content) for detailed listing and description of available data points.  

The connector provides a single capability using an IPv4/IPv6 address as input.

For additional details, and to register for an API key from the service provider, refer to the ipgregistry.co [API Documentation](https://ipregistry.co/docs/).

# Setup

## Resources

An ipregistry account and API Key is required to interact with the ipregistry API.

* Key ipregistry.co documentation:
  - [Sign-up for a free ipregistry.co Account](https://dashboard.ipregistry.co/signup)
  - [Quick Start Guide](https://dashboard.ipregistry.co/quickstart)
  - [API Documentation](https://ipregistry.co/docs/)

The ipregistry API key will be used within the ipregistry.co DaVinci connector configuration.

For information and setup help, see the following sections of the DaVinci documentation:

* DaVinci documentation:
  - [Importing a flow from the Flow Library](https://docs.pingidentity.com/csh?context=davinci_importing_a_flow_from_the_flow_library)
  - [Adding a connection](https://docs.pingidentity.com/csh?context=davinci_adding_a_connection)

## Setting up the connector

In DaVinci, add an ipregistry.co connection. For help, see [Adding a connection](https://docs.pingidentity.com/csh?context=davinci_adding_a_connection).

When using the import/export capabilities, the target Connectors must be installed in the target environment as a prerequisite prior to migrating a flow.  The import/export process cannot create an instance of a connector that does not exist in the environment.

### Connector settings

Configure the connector settings on the **General** tab:

* API Key:  
  The requests made to the Ipregistry API are identified by API keys. The API key is required, otherwise an error is returned.
  
# Using the connector in a flow

You can use sample flows as a starting point or create your own flows to satisfy your requirements. 

# Capabilities

### Single IP Lookup (ipLookup)


Performs a lookup of the provided IPv4/IPv6 address, returning aggregated geolocation and threat information.

#### IP Address `textField` `required`


IPv4/IPv6 address to lookup.

---



# Troubleshooting

If you are having issues with the ipregistry.co connector, you can try the following:

* Verify that the API Key is correct and enabled.
* For each connector in the flow, make sure that all of the mandatory inputs have been provided.
* Use the Analytics feature to see where the flow stopped.
* Select the Options icon, and turn on Show Node ID. This will make it easier to identify the source of inputs and outputs.
