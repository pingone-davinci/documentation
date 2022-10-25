
# The Jira service management connector


Author: Ganesh Raj

# Introduction

The Jira service management connector is a collaborative IT Service Management (ITSM) solution that lets you create requests based on certain actions.

You can use this Jira service management connector to:
Create a request
Update a request
Read queue requests
Read requests
Custom API Action

# Setup

## Resources

For information and setup help, see the following documentation:

### JIRA Service Management

Jira service management documentation: https://www.atlassian.com/software/jira/service-management

### DaVinci documentation:
Adding a connection: https://docs.pingidentity.com/csh?context=davinci_adding_a_connection

Importing a flow from the Flow Library: https://docs.pingidentity.com/csh?context=davinci_importing_a_flow_from_the_flow_library

## Requirements

To use the connector, you'll need:

1. A JIRA Service Management Application URL.
2. The Token for accessing the JIRA Service Management Application


# Using the connector in a flow

This Jira Service management is an ITSM (IT Service Management) software and from this connector, you can perform the following:
Create a request
Update a request
Read queue requests
Read requests
Custom API Action

No special flow configuration is needed. Add the capability you want and populate its properties according to the help text.

For capabilities that have a Query Parameters section, you can add any query parameters that are supported by the Jira API. For help, see the Jira Cloud platform REST API documentation.

# Capabilities

### Create a request (capabilityCreateRequest)


Create a new request in Jira Service Desk

#### JIRA Service Desk URL `textField` `required`


URL for JIRA Service Desk. Example: your-domain.atlassian.net

#### Bearer Authorization Token for JIRA Service Desk `textField` `required`


Bearer Authorization Token for JIRA Service Desk

#### Raw JSON for creating new JIRA service desk request `codeEditor`


Raw JSON body to create new JIRA service desk request. Example: {   "requestParticipants": ["qm:a713c8ea-1075-4e30-9d96-891a7d181739:5ad6d69abfa3980ce712caae"   ],   "serviceDeskId": "10",   "requestTypeId": "25",   "requestFieldValues": {     "summary": "Request JSD help via REST",     "description": "I need a new *mouse* for my Mac"   } }

---

### Update a request (capabilityUpdateRequest)


Update an existing request in Jira Service Desk

#### JIRA Service Desk URL `textField` `required`


URL for JIRA Service Desk. Example: your-domain.atlassian.net

#### Bearer Authorization Token for JIRA Service Desk `textField` `required`


Bearer Authorization Token for JIRA Service Desk

#### JIRA Service Desk Issue ID `textField`


Issue ID of JIRA service desk request

#### Raw JSON for updating JIRA service desk `codeEditor`


Raw JSON body to update JIRA service desk request. Example: {"id": "1","additionalComment": {"body": "I have fixed the problem."}}

---

### Read queue requests (capabilityReadRequests)


Read a list of all requests in a queue

#### JIRA Service Desk URL `textField` `required`


URL for JIRA Service Desk. Example: your-domain.atlassian.net

#### Bearer Authorization Token for JIRA Service Desk `textField` `required`


Bearer Authorization Token for JIRA Service Desk

---

### Read request (capabilityReadARequest)


Read a request in Jira Service Desk with ID

#### JIRA Service Desk URL `textField` `required`


URL for JIRA Service Desk. Example: your-domain.atlassian.net

#### Bearer Authorization Token for JIRA Service Desk `textField` `required`


Bearer Authorization Token for JIRA Service Desk

#### JIRA Service Desk Issue ID `textField`


Issue ID of JIRA service desk request

---

### Make Custom API Call to JIRA Service Desk (capabilityCustomAPIRequest)


Define a custom API call to JIRA Service Desk.

#### Endpoint `textField` `required`


The Jira Service Desk API endpoint, such as "/rest/api/3/<resource-name>".

#### Method `dropDown` `required`


The HTTP Method.


 - GET
 - POST
 - PUT
 - DELETE
 - PATCH

#### Query Parameters `keyValueList`


Add query parameters and provide their values.

#### Headers `keyValueList`


Add HTTP headers and provide their values.

#### Body `codeEditor`


The raw JSON body, such as "{ "Username": "jsmith@example.com", "ProfileId": "00e8a0000024zkjAAA" }".

---

