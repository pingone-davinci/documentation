# Akamai Account Protector Connector

## Introduction

The Akamai Account Protector connector for PingOne DaVinci lets you **ingest and evaluate Akamai risk signals** provided in the `Akamai-User-Risk` HTTP header. The connector parses the header, extracts the **user risk score** and related fields, and returns a **risk outcome** based on configurable thresholds.

## Setup

### Resources

For product details and deployment guidance, see Akamai’s documentation and your Akamai representative.

* [Akamai Account Protector](https://www.akamai.com/products/account-protector)

### Requirements

To use the Akamai Account Protector connector, you will need:

* **Akamai-User-Risk Header**
* **Risk Thresholds**
  * **Medium Risk Threshold** – scores **≤ this value** are categorized as **Low**.
  * **High Risk Threshold** – scores **greater than the Medium threshold but ≤ this value** are categorized as **Medium**.
  * Any score **above the High threshold** is categorized as **High**.

### Setting up the connector

* In PingOne DaVinci, open the **Akamai Account Protector** connector configuration.
* Provide the required properties:

  * **Akamai User Risk Header** (`akamaiUserRiskHeader`): The full value of the `Akamai-User-Risk` HTTP header.
  * **High Risk Threshold** (`highValueThreshold`): Maximum score for **Medium**; scores above this are categorized as **High**. (Default: `50`)
  * **Medium Risk Threshold** (`mediumValueThreshold`): Maximum score for **Low**; scores above this and up to the High threshold are categorized as **Medium**. (Default: `25`)

## Using the connector in a flow

After setup, you can use the connector to:

* **Parse the Akamai header** to extract the numeric **risk score** and additional signals (e.g., `uuid`, `username`, `risk`, `trust`, `action`).
* **Classify the score** into `LOW`, `MEDIUM`, or `HIGH` using your configured thresholds.
* **Branch the flow** using the `riskLevel` (e.g. allow on LOW, step-up on MEDIUM, deny on HIGH).

## Capabilities

### Evaluate Akamai Risk Score

Parses the `Akamai-User-Risk` HTTP header, extracts the **user risk score**, and assigns a **riskLevel** using your configured thresholds:

* **LOW** → `score <= mediumThreshold`
* **MEDIUM** → `score > mediumThreshold && score <= highThreshold`
* **HIGH** → `score > highThreshold`
