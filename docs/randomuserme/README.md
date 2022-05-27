# RandomUser.me Connector
Author: arno@pingidentity.com

# Introduction
Generate random user data

# Setup
## Resources
For information and setup help, see the following sections of the randomuser.me documentation:

## Documentation
https://randomuser.me/documentation

## Requirements
The randomuser.me service is free and open-source, no account or key required.

## Get User
1. Pick a gender or leave random
2. Set a seed to control which user you get

## Setting up the connector
No setup required, simply drop the connector in your flow and get a random user.

### Connector settings
No API key is required.

# Using the connector in a flow
You can use the connector in a variety of use cases, such as:

## Application testing
Get a random user to test that an application, service or API call works.


## Account provisioning stuffing
Some services may require data you do not have, just generate random data about the user and stuff that data in.

# Capabilities
### Get Random User (getRandomUser)


Generate random user data

#### Gender `dropDown`


Gender of the random user


 - Random
 - Male
 - Female

#### Seed `textField`


Seeds allow you to always generate the same user or set of users

---



# Limitations
Does not currently support bulk random user generation
