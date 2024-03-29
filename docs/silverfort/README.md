# Silverfort Connector

## Doc draft

Author: Davy De Mits, Solutions Architect Technical Alliances,  Silverfort



# Introduction

Silverfort Unified Identity Protection platform delivers modern identity security controls on top of your existing IAM infrastructure. 

Entity risk analysis is a key component of the security controls. Within the Silverfort platform, each entity involved in user and system authentication behavior is analysed for abnormal behavior, known threats, malicious activities, etc. 
Based on this analysis entities, for example a user account, get's a risk scoring assigned. The scoring is dynamic and constantly updated based on the behavioral indicators seen by the platform.

The Silverfort Davinci connectors allow ingestion and updates to the risk for entities within the Silverfort platform.



# Setup

## Resources

For information and setup help, see the following sections of the Silverfort documentation:


## Silverfort documentation
View the [Silverfort site](https://docs.silverfort.com) for further information on documentation and general information on the Silverfort platform.


## Requirements

To use the connector, you'll need:

* Silverfort Unified Identity Protection Platform
* Silverfort third party Risk enabled

## Setting up the connector

1. Configure risk API user and secrets in Silverfort
2. Enable API third party risk update in Silverfort
3. Complete the API connection and secrets in Davinci for the Silverfort connector (App User ID, App User Secret, Risk API Key)

# Capabilities
There are two capabilites in this connector. To set up either capability, look at the below information to do so:

* Get Entity Risk capability:
  * User Parameter (required): Choose between User Principal Name, Distinguished Name, and Resource Name
  * User Identifier (required): Will be sourced from a form earlier in the flow, value must match the format of the User Parameter chosen above
 
* Update Entity Risk capability:
  * User Parameter (required): Choose between User Principal Name, Distinguished Name, and Resource Name
  * User Identifier (required): Will be sourced from a form earlier in the flow, value must match the format of the User Parameter chosen above
  * Risk Update Name (requierd): Risk Update Name is the unique name of the risk update. Every risk update with the same name will overide the previous update
  * Severity (required): Choose between Low, Medium, High, Critical
  * Valif For (required): Length of time severity is valid for (in hours). Use integers, example: 2
  * Description (required): Enter reason for change in severity


# Using the connector in a flow

You can use the connector in a couple of different use cases, such as:
- Get risk from an entity in Silverfort
- Update risk for an entity in Silverfort


## Get risk from an entity in Silverfort

Davinci flows leveraging the 'Get Entity Risk' connector can retrieve risk for any entity during the processing of a certain activity. The risk retrieved from Silverfort through the connector gives valuable insights on the threat level of an entity, and allows critical decision making for subsequent flow handling.


## Update risk for an entity in Silverfort

The 'Update Entity Risk' capability allows Davinci flows to update the risk of an entity within the Silverfort platform. This for example influences the behavior of the Silverfort identity security policies and allows one to directly enforce a higher security level on users, enforce block policies for entities, introduce additional MFA for a critical entity, etc.


## Troubleshooting resources

### [Silverfort Support Desk]

Email: Support@silverfort.com
