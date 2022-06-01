# Postman Connector

Author: samirgandhi@pingidentity.com

# Introduction

[Postman](https://www.postman.com/) is an API platform for building and using APIs. Postman simplifies each step of the API lifecycle and streamlines collaboration so you can create better APIs—faster.
[Postman Collections](https://learning.postman.com/docs/getting-started/creating-the-first-collection/) are a group of saved requests.
The Postman Connector for Davinci allows you to run a Postman collection from within a Davinci Flow. This is useful for running a collection that is already created in Postman rather than rebuilding the work in Davinci.

# Setup

## Resources

For information and setup help, see the following sections of the Postman documentation:

- Postman
  - [Postman Homepage](https://www.postman.com/)
  - [Build Postman Collection](https://learning.postman.com/docs/getting-started/creating-the-first-collection/)

## Requirements

To use the connector, you'll need:

- [Postman](https://www.postman.com/downloads/)
- A [Postman Collection](<(https://learning.postman.com/docs/getting-started/creating-the-first-collection/)>)

## Export Collection and Variables

A Postman Collection uses environment variables to be more flexible. Export your desired collection and variable set(s) to be used in Davinci.

1. Export collections, environment variables, and global variables as json describe here: https://learning.postman.com/docs/getting-started/importing-and-exporting-data/

2. Optional, share collection as public url as described here: https://learning.postman.com/docs/collaborating-in-postman/sharing/#sharing-postman-entities

## Setting up the connector

In SDavinci, add a **Postman** connection. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector settings

#### Global Variables

Exported JSON of Global variables from a Postman Workspace.

# Using the connector in a flow

The connector is used in a flow to run a collection. After completion the connector returns the status of all requests and details on any failed assertions.

# Capabilities

### Run Collection (runCollection)


Run an Postman collection passed as JSON

#### Collection `codeEditor`


Exported JSON blob or {"url":"<link>"} of collection to be used for iteration

#### Environment Variables `codeEditor`


Environments provide a set of variables for use within collections. JSON blob of an environment exported from postman

---
