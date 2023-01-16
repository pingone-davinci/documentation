
# BeyondTrust Connector


Author: BeyondTrust


# Introduction

Privileged remote access is about ensuring employees, third-party vendors, and other insiders don't have free access to systems while accessing the network remotely.

You're able to define who has permissions, when they have it, and the appropriate level of access each role needs to complete their work. This ensures privileges aren't left unchecked, and prevents users from becoming entry points for attacks.


# Setup
To set up the connector,  you will need to first create an API account in your PRA instance:  https://www.beyondtrust.com/docs/privileged-remote-access/getting-started/admin/api-configuration.htm.  Under permissions, select full access for the command and reporting api.  Take note of the OAuth Client ID and Secret.



## Resources

For information and setup help, see the following sections of the PRA documentation:

- https://www.beyondtrust.com/docs/privileged-remote-access/getting-started/deployment/cloud/index.htm
- https://www.beyondtrust.com/docs/privileged-remote-access/how-to/index.htm
- https://www.beyondtrust.com/docs/integrations/index.htm?prod=Privileged-Remote-Access


## Requirements

To use the connector, you'll need:

* API account in PRA
* Client ID and Secret for API account 


### Connector settings

In the connector settings, under General, provide the following:
PRA Web API URL - The url of the PRA instance (For example https://customerpra.beyondtrustcloud.com)
Client ID - The client ID of the api account created in PRA for use with this connector
Client Secret - The client secret of the api account created in PRA for use with this connector


# Using the connector in a flow

You can use the connector in two workflow use cases:
- a security incident has occurred on a host that requires any remote sessions to it be terminated.
- a security incident has occurred by a user, and any remote session that use may have across the infrastructure be terminated. 

The security incident may be discovered by any other 3rd party vendors DaVinci connector, such as XDR, SOAR etc, and then supply the PRA connector with a hostname and/or identity.  The PRA connector provides a result (error or success) which can potentially flow into an ITSM tool as part of the workflow using their connector. 

## Use Case

The connector gives an organization the ability to terminate all PRA sessions on a host (by hostname) and/or terminate all PRA sessions a particular identity (by username) may have across any host.   The hostname and/or username can be provided to the connector though a HTML form, or can be fed directly into the connector as part of a larger workflow. 


# Capabilities

### Terminate PRA Jump Session by Hostname (terminateSessionsByHostname)


Terminate PRA Jump Session by Hostname

#### Hostname `textField`


Name of the machine for which you would like to terminate all open sessions

---

### Terminate PRA Jump Session by Username (terminateSessionsByUsername)


Terminate PRA Jump Session by Username

#### Username `textField`


Username for which you would like to terminate all open sessions

---


