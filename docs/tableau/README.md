# Tableau Connector

Author: Ganesh Raj

# Introduction

With the Tableau Server REST API you can manage and change Tableau Server, Tableau Online site, and Prep Conductor resources programmatically, using this Davinci connector, you can perform the capabilities as mentioned below

-Add Data Source to Schedule    Adds a task to refresh a data source to an existing schedule.
-Add Workbook to Schedule    Adds a task to refresh or accelerate a workbook to an existing schedule.
-Cancel Job    Cancels a job specified by job ID.
-Create Schedule    Creates a new schedule on Tableau Server.
-Delete Extract Refresh Task    Deletes an extract refresh task
-Delete Schedule    Deletes the specified schedule.
-Get Extract Refresh Task    Returns information about the specified extract refresh task.
-Get Extract Refresh Tasks in a Schedule    Returns a list of the extract refresh tasks for a specified schedule on the specified site.
-Get Extract Refresh Tasks in a Site    Returns a list of extract refresh tasks for the site.
-Get Schedule    Returns detailed information about the specified schedule.
-Query Job    Returns status information about an asynchronous process that is tracked using a job.
-Query Jobs    Returns a list of active jobs on the specified site.
-Query Schedules    Returns a list of flows, extract and subscription schedules.
-Run Extract Refresh Task    Runs the specified extract refresh task.
-Update Schedule    Modifies settings for the specified schedule, including the name, priority, and frequency details.

## Flows
Capability: Add Flow Permissions
Capability Subtitle: Add permission to the specified flow for a Tableau Server user or group.


## Users & Groups
Capability: Add User to Site
Capability Subtitle:  Adds a user to Tableau and assigns the user to the specified site
Capability: Get Groups for a User
Capability Subtitle: Gets a list of groups of which the specified user is a member.
Capability: Add User to Group
Capability Subtitle: Adds a user to the specified group
Capability: Remove User from Group
Capability Subtitle: Removes a user from the specified group.
Capability: Read User
Capability Subtitle: Returns information about the specified user.
Capability: Remove User from Site
Capability Subtitle: Removes a user from the specified site.


# Setup

## Resources

For information and setup help, see the following sections of the tableau documentation: https://help.tableau.com/current/server/en-us/install_config_top.htm


DaVinci documentation:
Adding a connection: https://docs.pingidentity.com/csh?context=davinci_adding_a_connection
Importing a flow from the Flow Library: https://docs.pingidentity.com/csh?context=davinci_importing_a_flow_from_the_flow_library


## [Link to resources from the service documentation

## Requirements

To use the connector, you'll need:




server-url
- The tableau server URL Example: https://www.tableau.com:8030

api-version
- The version of the API to use, such as 3.16.

datasource-id
- The ID of the flow.

group-id
- The ID of the group.

job-id
- The ID of the job.

schedule-id
- The ID of the schedule that you are associating with the data source.

site-id
- The ID of the site that contains the view.

task-id
- The ID of the extract refresh task.

user-id
- The ID of the user to get information for.

## [Task name]

1. A tableau server URL.
2. The Token for accessing the tableau server REST API.

### Connector settings

[List and explain the connector settings that appear when the connection is opened from the **Connections** page. If you did not cover it earlier in the **Setup** section, tell the user how to complete each configuration field or where to get the information they need.

These typically on the **General** tab, but some connectors have a different name or multiple configuration tabs. Don't document **Capabilities**, or **In Flows**.]

# Using the connector in a flow
Add Data Source to Schedule
- Adds a task to refresh a data source to an existing schedule.

Add Workbook to Schedule
- Adds a task to refresh or accelerate a workbook to an existing schedule.

Cancel Job
- Cancels a job specified by job ID.

Create Schedule
- Creates a new schedule on Tableau Server.

Delete Extract Refresh Task
- Deletes an extract refresh task

Delete Schedule
- Deletes the specified schedule.

Get Extract Refresh Task
- Returns information about the specified extract refresh task.

Get Extract Refresh Tasks in a Schedule
- Returns a list of the extract refresh tasks for a specified schedule on the specified site.

Get Extract Refresh Tasks in a Site
- Returns a list of extract refresh tasks for the site.

Get Schedule
- Returns detailed information about the specified schedule.

Query Job
- Returns status information about an asynchronous process that is tracked using a job.

Query Jobs
- Returns a list of active jobs on the specified site.

Query Schedules
- Returns a list of flows, extract and subscription schedules.

Run Extract Refresh Task
- Runs the specified extract refresh task.

Update Schedule
- Modifies settings for the specified schedule, including the name, priority, and frequency details.

Add Flow Permissions
- Add permission to the specified flow for a Tableau Server user or group.

Add User to Site
- Adds a user to Tableau and assigns the user to the specified site.

Get Groups for a User
- Gets a list of groups of which the specified user is a member.

Add User to Group
- Adds a user to the specified group.

Remove User from Group
- Removes a user from the specified group.

Read User
- Returns information about the specified user.

Remove User from Site
- Removes a user from the specified site.

Update User
- Modifies information about the specified user.


No special flow configuration is needed. Add the capability you want and populate its properties according to the help text.



## [Use case]

Actions that are described above can be performed in this Davinci Connector. For more information, Please go through documentation: https://help.tableau.com/current/api/rest_api/en-us/REST/rest_api.htm

# Capabilities

Leave this section blank: it will be generated automatically

# Troubleshooting

You can test each capability individually. For help, see [Testing capabilities](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).
