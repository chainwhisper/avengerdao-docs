---
title: Integration Guide
sidebar_position: 3
---

# AvengerDAO Meter Integration Guide for Security Providers

Welcome to the AvengerDAO Meter integration guide for security providers. This guide is designed to help you understand the process of integrating your security service with the AvengerDAO Meter API. Please read the following instructions carefully and ensure that your service meets the prerequisites before proceeding with the [integration](endpoints.md).

### Prerequisites

**Before integrating with the AvengerDAO Meter API, security providers must fulfill the following prerequisites**

- Provide a trust_score: Your service must be able to calculate and provide a trust score for a given address. The trust score should range from 0 to 100, with higher scores indicating a higher level of trust. The trust scores are mapped to trust bands as follows:

  - Very Low: 0-20
  - Low: 21-60
  - Medium: 61-90
  - High: 91-99
  - Very High: 100

  Make sure to consider these trust bands when providing the trust score, as they help API consumers to interpret the scores more accurately.

- Provide risk factors: Along with the trust score, your service must also provide the risk factors that influenced the score. These factors should be presented as a JSON object with details about each risk factor, including its name, value, risk level, and a brief description.

- Consider the async response: If your service does not have data for a specific address, it should return an asynchronous response indicating that the result is not yet available. In this case, the API consumer will need to poll your service at the recommended interval until a definite result is available.

- Be cautious when giving a 100 score: A perfect trust score of 100 should be given only when the address has been thoroughly vetted and determined to be completely trustworthy. Exercise caution and ensure that all risk factors have been taken into account before assigning a score of 100.

- Provide documentation for risk_details: Your service must provide clear documentation listing all possible risk details that can be returned, allowing us to map them to our internal database entries and produce the best results for our clients.

- Provide information on data collection: Give a clear understanding of how your API collects security information on addresses and an estimation of the current number of addresses that your API has data for.

**It is essential to emphasize the importance of these prerequisites, as meeting them is critical to ensuring a successful and seamless integration with the AvengerDAO Meter API.**

### Integration Process

#### To ensure a smooth integration process, follow these steps:

- Step 1: Understand the API Specification

  Familiarize yourself with the API request and response structure, as well as the synchronous and asynchronous response types. Make sure your service can handle and return data in the format expected by the AvengerDAO Meter API.

- Step 2: Implement the Required Functionality

  Update your service to provide the necessary data in the expected format, including trust scores, risk factors, and support for asynchronous responses when data is not available for a given address. Ensure that your API follows the authentication mechanism specified in the AvengerDAO Meter API [documentation](../consumer-api/authorization.md).

- Step 3: Testing and Feedback

  After implementing the required functionality, notify the AvengerDAO team so that they can perform testing from their side. They will provide feedback on any issues or required changes. Once any necessary adjustments are made and the integration is successful, the AvengerDAO team will enable your service in production.

By following this guide and ensuring that your service meets the prerequisites, you can successfully integrate with the AvengerDAO Meter API and provide valuable security data to the community.