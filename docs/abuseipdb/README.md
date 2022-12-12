# AbuseIPDB Connector


Author: Ryan Schafer


# Introduction

The AbuseIPDB connector identifies IP addresses that have been associated with malicious activity online. This connector takes an IP Address as an input value and runs it against the AbuseIPDB API to determine if users IP address is from a bad actor.


# Setup


## Resources

For background information on the API utilized through this connector, see the following documentation from the AbuseIPDB site:


 https://docs.abuseipdb.com/#introduction


## Requirements

To use the connector, you'll need:


* An AbuseIPDB tenant (to gather an API Key)
* A DaVinci tenant


## Configuration Steps


1. Set up an account at https://www.abuseipdb.com/register?plan=free. This is the free level and gives you access to 1000 API calls, but there are other paid plans available for additional access.
2. Once an account has been set up, on your account page go to the API tab and create an API Key. This will be required to configure the connector within DaVinci.
3. Add the connector to your library via the "Connections" tab in DaVinci by searching for it and selecting "Add". Click on the newly added connector in your library once done and add the API key to the "General" page. This connector is now configured and can be used within a flow on the "Flow Studio" tab.


# Using the connector in a flow

You can use the connector primarily to:


## Verify IP Address

Verify whether an IP Address from an end user is from a bad actor or is safe.


# Capabilities

### Get Single IP Address (getSingleIp)


Returns datapoints around a single IP Address

#### Max Days `textField`


Maximum amount of days to look back to

#### IP Address `textField`


IP Address

---


# Limitations

This connector will only be able to verify a single IP Address at a time.
