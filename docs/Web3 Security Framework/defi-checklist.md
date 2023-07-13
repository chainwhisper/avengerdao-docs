

# Decentralized Finance Practices Checklist

Classification: **Restricted**

**Stage: Enquiry stage (40)**

**Introduction**:

The Web3 Security Framework Initiative is a collaborative effort to promote the adoption of best practices in web3 security. The initiative aims to minimize the risks associated with security vulnerabilities and hacks, which have become increasingly prevalent in the web3 space. Moreover, projects that demonstrate full compliance with our rigorous guidelines will earn an on-chain certificate recognized by all the AvengerDAO members on the BNB Chain ecosystem.

This document serves as a comprehensive checklist of the critical elements surrounding the secure development of DeFi decentralized applications.

|         |                                                              |             |                       |          |
| ------- | ------------------------------------------------------------ | ----------- | --------------------- | -------- |
| Item ID | Security Check                                               | Criticality | Is Project Compliant? | Comments |
| **1**   | **General**                                                  |             |                       |          |
| 1.1     | Verify that the decentralized application (Dapp) does not assume users can only send tokens using its smart contract functions. Tokens can be sent using the token smart contract transfer function or a self-destruct mechanism. | TBD         |                       |          |
| 1.2     | Certify the separation of the deposit logic from the reward calculation as reserves might impact the calculation. | TBD         |                       |          |
| 1.3     | Certify there are mechanisms to pause the contracts in case of the detection of a compromised dependency such as oracles. | TBD         |                       |          |
| **2**   | **Oracle based services**                                    |             |                       |          |
| **2.1** | **Spot price manipulation**                                  |             |                       |          |
| 2.1.1   | When using an on-chain price calculation mechanism, certifying the price of an asset cannot be manipulated in the same transaction, manipulating the source data, via flash loans for instance. | TBD         |                       |          |
| 2.1.2   | Ensure the on-chain price calculation does not rely on sources with low liquidity, such as limited liquidity pools. | TBD         |                       |          |
| 2.1.3   | Certify the usage of a secure calculation mechanism such as time-weighted average prices. | TBD         |                       |          |
| **2.2** | **Centralized Oracles**                                      |             |                       |          |
| 2.2.1   | Entrusting centralized entities with the responsibility of feeding data to smart contracts is risky. Only rely on such service as last resort. In such, cases, important due diligence can be done such as: Certify the entity's reputation and data correctness. | TBD         |                       |          |
| 2.2.2   | Verify they aren’t using data from other sources without proper verification. | TBD         |                       |          |
| 2.2.3   | Verify the centralized actor cannot be incentivized to push altered data to the data source. | TBD         |                       |          |
| **2.3** | **Off-chain Oracles**                                        |             |                       |          |
| 2.3.1   | Such oracles ensure the aggregation of off-chain data and validate them prior to pushing them on-chain. Such services rely on regular web2 infrastructure and before using their services, it is important to certify they are secure against any vulnerability described in the OWASP vulnerability catalog and that they follow Coding Securing Guidelines. | TBD         |                       |          |
| **2.4** | **On-chain Oracles**                                         |             |                       |          |
| 2.4.1   | Ensure the on-chain oracle solution uses a community-driven dispute mechanism, pre-commit, or any feedback mechanism that enables a second layer validation prior to pushing data on-chain. | TBD         |                       |          |
| **3**   | **Lending Pools**                                            |             |                       |          |
| 3.1     | Ensure only a specific function in the lender smart contract is called when performing a flash loan. | TBD         |                       |          |
| 3.2     | Prevent reentrancy attacks in your flash loan function.      | TBD         |                       |          |
| 3.3     | Certify the mechanism calculating the number of tokens before and after the loans is not vulnerable. | TBD         |                       |          |
| 3.4     | Verify that it is not possible to withdraw tokens from the pool balance, during a flash loan. | TBD         |                       |          |
| **4**   | **Liquidity Pools**                                          |             |                       |          |
| 4.1     | Ensure that the asset price calculation mechanisms cannot be attacked by price oracle manipulation. | TBD         |                       |          |
|         |                                                              |             |                       |          |
| 4.2     | Verify calculations are done with enough precision decimals. | TBD         |                       |          |
| 4.3     | If using an external oracle, certify the service provider is trustworthy. | TBD         |                       |          |
| 4.4     | A pause mechanism to prevent service to continue working in abnormal conditions. | TBD         |                       |          |
| 4.5     | Ensure LP with deflationary tokens use a secure mechanism to update their rate and it cannot be updated in the same transaction. | TBD         |                       |          |
| **5**   | **Governance**                                               |             |                       |          |
| 5.1     | Verify if the decentralized application governance smart contract has a mechanism to prevent malicious actors from obtaining and controlling a majority of governance tokens in the market via flash loans. | TBD         |                       |          |
| 5.2     | Ensure the contract is a Governance standard that has been fully tested. | TBD         |                       |          |
| 5.3     | Ensure secure management of the project via a DAO or a multisig contract. | TBD         |                       |          |
| 5.4     | Certify the counting of votes is done correctly and according to what has been stipulated in the protocol. | TBD         |                       |          |
| 5.5     | Ensure the usage of delays and interruption mechanisms exist in case of unexpected situations. | TBD         |                       |          |
| 5.6     | Prioritize the usage of a 2-step transfer mechanism for governance tokens to address flash loan attack risks. | TBD         |                       |          |