

# Clockify Connector

Author: Matthew Teets

# Introduction
Clockify allows users to push and pull data to and from a specified Clockify workspace.

### Capabilities:

##### Client Capabilities
* `Create Client`
* `View Client`
* `Update Client`
* `Delete Client`

##### Project Capabilities
* `Create Project`
* `View Project`
* `Update Project`
* `Delete Project`

##### Time Entry Capabilities
* `Start Timer`
* `Stop Timer`

##### Custom Capabilities
* `Make Custom API Call`

# Setup

## Resources

#### For information and additional help, see the following sections of the Clockify API documentation:
Clockify Capabilities API Documentation:
   * [Clockify API Reference](https://clockify.me/developers-api)

Client Capabilities
  * [Create Client](https://clockify.me/developers-api#:~:text=Client-,Add%20a%20new%20client,-POST%20/workspaces/%7BworkspaceId)
  * [View Client](https://clockify.me/developers-api#:~:text=Find%20clients%20on%20workspace)
  * [Update Client](https://clockify.me/developers-api#:~:text=Client-,Update%20client,-PUT%20/workspaces/%7BworkspaceId)
  * [Delete Client](https://clockify.me/developers-api#:~:text=Client-,Delete%20client,-DELETE%20/workspaces/%7BworkspaceId)

Project Capabilities
  * [Create Project](https://clockify.me/developers-api#:~:text=Project-,Add%20a%20new%20project,-POST%20/workspaces/%7BworkspaceId)
  * [View Project](https://clockify.me/developers-api#:~:text=Get%20all%20projects%20on%20workspace)
  * [Update Project](https://clockify.me/developers-api#:~:text=Update%20project%20on%20workspace)
  * [Delete Project](https://clockify.me/developers-api#:~:text=Delete%20project%20from%20workspace)

Time Entry Capabilities
  * [Start Time](https://clockify.me/developers-api#:~:text=Time%20entry-,Add%20a%20new%20time%20entry,-If%20end%20is)
  * [Stop Time](https://clockify.me/developers-api#:~:text=Stop%20currently%20running%20timer%20on%20workspace)
   
DaVinci Documentation:
  * [Login to DaVinci](https://portal.singularkey.com/dashboard)
  * [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
  * [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)


## Requirements

#### To use the Clockify connector:
* You must have access to a configured Clockify account.
   * Or create a new account [here](https://app.clockify.me/en/signup).
* You must also have access to a configured Clockify Workspace.
	* Or create a new Clockify workspace by following the documentation [here](https://clockify.me/help/users/workspaces#:~:text=Anyone%20can%20create%20a%20new,remove%20people%20from%20Admins%20group).
* Once your account and workspace are setup you must have a valid API key to make any calls to the Clockify API.
   * Your API Key can be found at the bottom of the following page [here](https://app.clockify.me/user/settings#:~:text=personal%20API%20key.-,API%20key,-Generate).
	   * If no API Key is inside the text field click `Generate` to create a new API Key.

## Setting up the connector

#### Clockify Connector General Settings:
* Navigate to the Clockify connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner.
* Search for the desired connector (in this case, Clockify).
* Select the Clockify connector.
* Once the Clockify connector has been added to the _**Your Connections**_ list, click on the connector.
* From here you will see three empty text fields labeled `API Key`, `API Version`, and `Workspace ID` .
   * **API Key**:
      * Simply copy and paste your Clockify API Key into this text field.
  * **API Version**:
	  * This field will already be filled out.
		  * Only change this if the API version becomes out dated.
  * **Workspace ID**
	  * Copy and paste the ID of the Clockify workspace you wish to use with DaVinci into this text field.
		  * Your workspace ID can be found by navigating to your workspace settings, and copying the unique 24-char part inside the URL.
			  * It will look something like this: `73b4i8c6a3e51825zf2da10i`
 * Click **Apply**
# Using the connector in a flow

### Some Clockify connector use cases:
* Initiate a new time entry to determine how long a certain task takes.
* Stop a time entry that was started within the same DaVinci flow.
* Create a new project from inside a DaVinci flow.

### Clockify API Request Requirements:
* You must have a fully functioning and configured Clockify account and workspace.
* The `API Key`, `API Version`, and `Workspace ID` fields must be correctly filled out in the connector settings.

---

### Simple Use Case - initiate a new time entry within a DaVinci Flow:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select **Blank Flow**, then click save.
* Once inside the flow sandbox add the Clockify connector and select the `Start Timer` capability.
* This Clockify capability has three capability level properties: `Time Entry Description`, `Time Entry Billable Status`, `Project ID`.
* These can be filled out 1 of 2 ways:
   1. Manually inserting the desired values into the respective fields.
   2. Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* The capability level properties are represented by the following:
	* `Time Entry Description` is a short note or description regarding the time entry.
	* `Time Entry Billable Status` is a togglable property that either sets the time entry to be billable or not.
		* Off = not billable
		* On = billable.
	* `Project ID` is the ID of the desired project you with to assign to this time entry.
* Once the connector is configured and executed it will begin a timer inside your Clockify workspace.
* The Clockify connector does not generate any output on its own.
   * To see the HTTP response object returned from the Clockify API you can do the following:
      * Add an HTTP block after your Clockify connector. 
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Clockify connector option with the `Start Timer` capability listed.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click **Save**, **Deploy**, and **Run**.

---

### Simple Use Case - stop a time entry that was started within the same flow:
* Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
* Insert the desired name and description and click next.
* Select Blank Flow, then click save.
* Once inside the flow sandbox add the Clockify connector and select the `Stop Timer` capability.
* This Clockify capability has one capability level property: `User ID`
* This can be filled out 1 of 2 ways:
   1. Manually inserting the desired values into the respective fields.
   2. Selecting the appropriate output variables from a previous connector via the angle bracket button ( **{}** ).
      * E.g. an HTTP connector with an HTML form that prompts the user for the desired values.
* The capability level property is represented by the following:
	* `User ID` is the ID of the user who started the time entry you wish to stop.
		* This can be obtained from a Clockify connector that has the `Start Timer` capability.
		* Simply open the `Stop Timer` capability and click on the angle bracket button located inside the `User ID` text field.
		* From the drop-down menu locate and click on the Clockify connector that is using the `Start Timer` capability.
		* Finally, from the `output` drop-down select the `user_id (string)` output property.
			* The `user_id` corresponds to the user that started the time entry.
		* Then click **Apply**
* Once the connector is configured and executed it will stop the time entry started inside the DaVinci flow.
* The Clockify connector does not generate any output on its own.
   * To see the HTTP response object returned from the Clockify API you can do the following:
      * Add an HTTP block after your Clockify connector. 
      * Click on the Custom HTML Message capability.
      * In the _**Message**_ text area select the circular angel bracket button ( **{}** )
         * From the dropdown, select the Clockify connector option with the `Stop Timer` capability listed.
         * Choose the `output (object)` by clicking `(+)`.
      * `Click apply`
* In the upper right hand corner click Save, Deploy, and Run.

---

# Capabilities

Leave this section blank: it will be generated automatically
