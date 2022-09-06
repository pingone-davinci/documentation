
# Introduction

At [443ID](https://443id.com/), we firmly believe that risk analysis can’t be a one size fits all. 443ID connects identity security professionals on any digital platform to OSINT data. Open Source Intelligence (OSINT) data brings important outside context to the identity conversation – letting anyone make more nuanced decisions about how to authenticate, register, or authorize their users. The 443ID platform makes OSINT data actionable through a simple API and key IAM platform integrations at a price anyone can afford.

# Setup

To add the connector you will first need to ensure you have an active PingIdentity account and a 443ID account to continue. (Information on how to setup your 443ID account below)

## Resources

+ 443ID documintaion
    - [Product Documentation](https://docs.443id.com/docs/443id/rmp4oexe47nra-overview)
+ DaVinci documentation
    - [Adding a connection](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)
    - [Importing a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)


## Requirements

To use the connector, you'll need:

* An active 443ID account and tenant where you have administrative privileges. To set up a new 443ID account, please follow this [here](https://app.443id.com/?utm_source=auth_0)


## Set up 443ID

To configure the integration with 443ID, follow the steps below:

Head over to [443ID](https://app.443id.com/?utm_source=auth_0), where you can sign up for an account.

* Once setup is complete, you will use your API KEY to configure your own policy or use one of the starter policies that we provide.

* Want to create a custom policy? Learn more about building and testing a custom policy [here](https://docs.443id.com/).

![API IMG](https://stoplight.io/api/v1/projects/cHJqOjEzMjg2MQ/images/IIbh4wa5Wk0)


## Setting up the 443ID connector

In DaVinci, add a **443ID Risk** connection. For help, see [Adding a connection](https://docs.pingidentity.com/csh?context=davinci_adding_a_connection).


### Connector configuration

* **API KEY**: Each time your application makes a request to get a 443ID score, it authenticates with an API key so we know which 443ID policy to apply. This API Key can be found in your 443ID policy (Edit Policy > Applications > Copy API Key).

![Screen Shot 2022-08-31 at 1.53.05 PM.png](https://stoplight.io/api/v1/projects/cHJqOjEyNTY1OA/images/Z1HNWu0LHCw)



# Using the connector in a flow
Authenticating & Assess users with 443ID Davinci Connector

![Screen Shot 2022-08-31 at 1.56.23 PM.png](https://stoplight.io/api/v1/projects/cHJqOjEyNTY1OA/images/quhcRpulIrI)

In this flow, an HTML form gathers user data and stores it in variables.

![Screen Shot 2022-09-01 at 10.58.32 AM.png](https://stoplight.io/api/v1/projects/cHJqOjEzMjg2MQ/images/N79fU7o5sdM)

Next the connector directs the browser to the 443ID Risk Score endpoint where you will use the data stored in the variables to submit the users information.
<!-- theme: info -->

> 
>
> Be sure to select the correct identifier for the correct fields. (This is an example and the IP address should come from the global variable)


![Screen Shot 2022-09-01 at 11.05.59 AM.png](https://stoplight.io/api/v1/projects/cHJqOjEzMjg2MQ/images/lGsSMPbkIyY)


Once the users information is passed to the endpoint and assessed against our OSINT Signals it will be passed along to the function call that will determin the next step in the users journey.
(Below is the 443ID endpoint Architecture)

![Screen Shot 2022-09-02 at 4.36.27 PM.png](https://stoplight.io/api/v1/projects/cHJqOjEzMjg2MQ/images/R3HlKKSQOr0)



Here we have our Function connector that checks if value A equals value B. Value A is fed in from the 443ID connector. Value B is the Minimum friction threshhold you would like to start requiring MFA. We set the default to `HIGH`. This can be configured to fit your needs. 

![Screen Shot 2022-09-01 at 10.54.22 AM.png](https://stoplight.io/api/v1/projects/cHJqOjEyNTY1OA/images/lDtHu2THxBw)

<!-- theme: danger -->

> #### For example: 
>
> If the users data comes back as `HIGH` they will be asked to MFA. 

![Screen Shot 2022-09-01 at 11.32.31 AM.png](https://stoplight.io/api/v1/projects/cHJqOjEzMjg2MQ/images/fmaEpYKTpjc)

<!-- theme: success -->

> #### Verification Succesful!
>
> Otherwise they will have a succesfull login.

![Screen Shot 2022-09-01 at 11.56.26 AM.png](https://stoplight.io/api/v1/projects/cHJqOjEzMjg2MQ/images/FYGzwPkMWg0)



### You can use the connector in a variety of use cases, such as:


## Adaptive MFA

The 443ID risk score may be used in authentication flows to reduce friction caused by MFA. 




## Secure Transaction Fraud Prevention

The 443ID risk score may also be used to prevent highly risky email addresses and/or phone numbers to be used for security sensitive flows such as MFA enrollment and password recovery. 

## Registration Fraud Prevention

Detect registration attempts from bots or suspicious users and prompt for additional verification before creating the account.


# Troubleshooting

For any issues regarding this integration please contact us via email at [support@443id.com](mailto:support@443id.com) or join our [Slack channel](https://join.slack.com/t/443id-beta/shared_invite/zt-17wfzshmc-BvGNNGKN0tFByVlQJiV2Rw).



### Testing capabilities

You can test each capability individually. For help, see [Testing capabilities](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).



