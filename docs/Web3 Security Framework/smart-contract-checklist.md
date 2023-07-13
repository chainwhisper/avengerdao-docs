# Smart Contract Security Checklist

Classification: **Restricted**

**Stage: Enquiry stage (40)**

**Introduction**:

The Web3 Security Framework Initiative is a collaborative effort to promote the adoption of best practices in web3 security. The initiative aims to minimize the risks associated with security vulnerabilities and hacks, which have become increasingly prevalent in the web3 space. Moreover, projects that demonstrate full compliance with our rigorous guidelines will earn an on-chain certificate recognized by all the AvengerDAO members on the BNB Chain ecosystem.

This document serves as a comprehensive checklist of the critical elements surrounding the secure development of solidity smart contracts.

| **Item id** | **Security Check**                                           | **Criticality** | **Is Project Compliant?** | **Comments** |
| ----------- | ------------------------------------------------------------ | --------------- | ------------------------- | ------------ |
| **1**       | ***Audit\***                                                 |                 |                           |              |
| 1.1         | To reduce risks of vulnerabilities, audits are required for each major release. The audits should be performed by multiple auditing firms. | High            |                           |              |
| 1.2         | Audits scope should be comprehensive and include business logic correctness, proxy setup, access control, vulnerability findings, etc. | High            |                           |              |
| 1.3         | Following the audits, ensure all issues have been fixed and recommendations have been implemented. | High            |                           |              |
| 1.4         | Ensure your project is part of a bug bounty program          | Medium          |                           |              |
| **2**       | ***Test Coverage\***                                         |                 |                           |              |
| 2.1         | All non-trivial functions should be tested.                  | High            |                           |              |
| 2.2         | Business-critical functions should be thoroughly tested against all edge cases. | High            |                           |              |
| 2.3         | Certify the exactitude of the expected behavior of functions and business flows. | High            |                           |              |
| 2.3         | Certify that all scenarios raising exceptions are also tested and that exception management works as expected (eg: matching internal exceptions with customer-facing error code/message) | High            |                           |              |
| 2.4         | Verify the code specifications using formal verification.    | Medium          |                           |              |
| **3**       | ***Solidity Specifics\***                                    |                 |                           |              |
| **3.1**     | **General**                                                  |                 |                           |              |
| 3.1.1       | Ensure development teams use security scanning tools.        | High            |                           |              |
| 3.1.2       | Use BSCSCan to verify all deployed contracts and their implementation | High            |                           |              |
| 3.1.3       | Verify smart contracts are not using send() or transfer() functions to send infrastructure tokens. | Medium          |                           |              |
| **3.2**     | **Immutability**                                             |                 |                           |              |
| 3.2.1       | Ensure smart contracts do not rely on the immutability of another smart contract, if the latter has a self-destruct or delegate-call mechanism. | High            |                           |              |
| **3.2**     | **Data**                                                     |                 |                           |              |
| 3.2.1       | Blockchain ledgers are publicly accessible by design. Therefore it is recommended that smart contract data should be classified according to its level of confidentiality. | High            |                           |              |
| 3.2.2       | Verify the confidentiality framework applied to the decentralized application data complies with regulations around the world. eg: GDPR, PCI-DSS, etc. | High            |                           |              |
| 3.2.3       | Ensure smart contracts' critical business logic does not rely solely on data that can be predictable or manipulated by validators, such as block timestamp, block number, block hash… | High            |                           |              |
| **3.3**     | **Complex Data Structure**                                   |                 |                           |              |
| 3.3.1       | Ensure the size of data stays stable over time so that gasconsumption remains stable. | Medium          |                           |              |
| 3.3.2       | Ensure proper validation of data to prevent runtime exceptions such as stack overflow, out of gas, and stack too deep. | Medium          |                           |              |
| **3.4**     | **Dependencies**                                             |                 |                           |              |
| 3.4.1       | Certify all decentralized applications' external dependencies are trusted sources. | High            |                           |              |
| 3.4.2       | Ensure such dependencies have been properly tested before integrating them. | Medium          |                           |              |
| 3.4.3       | Smart contract dependencies such as Libraries should be clearly identified and documented. | High            |                           | `            |
| 3.4.4       | Ensure dependency versions are clearly specified.            | Low             |                           |              |
| **3.5**     | **Business Logic**                                           |                 |                           |              |
| 3.5.1       | Ensure that whenever feasible, standard contracts are employed. | High            |                           |              |
| 3.5.2       | Certify that all crucial business flows are documented and comprehensively tested to avoid bugs and corner case exceptions. | High            |                           |              |
| 3.5.3       | Given the existence of front-running possibilities, and the risk of flash loan attacks, use adequate means to secure them. | High            |                           |              |
| 3.5.4       | Ensure the smart contract state is updated correctly when performing actions such as transfer, deposit, withdraw, etc… | High            |                           |              |
| 3.5.5       | Ensure that timelocks are used in relevant business flows where it makes sense. So that the projects have time to better observe and monitor decentralized applications app behavior and changes. It should be analyzed on a case-by-case basis. | Medium          |                           |              |
| **3.6**     | **Arithmetics**                                              |                 |                           |              |
| 3.6.1       | Certify that your arithmetic operations are protected against unwanted underflow or overflow. | High            |                           |              |
| 3.6.2       | Verify the inequalities are used when comparing smart contract balance. | High            |                           |              |
| 3.6.3       | Verify the order of magnitude of calculations is correct.    | High            |                           |              |
| 3.6.4       | Ensure the order of operations so that results do not lose precision. | High            |                           |              |
| 3.6.5       | Ensure divisions with integers are done safely.              | High            |                           |              |
| **3.7**     | **Input validation**                                         |                 |                           |              |
| 3.7.1       | Ensure user-defined inputs are sanitized and checked as soon as possible in the smart contract function code. | High            |                           |              |
| 3.7.2       | For input validation, ensure the usage of require or revert. | High            |                           |              |
| 3.7.3       | To prevent privilege escalation and replay attacks, functions utilizing off-chain signed cryptographic signatures for authorization must ensure that the signature is not susceptible to reuse. | High            |                           |              |
| 3.7.4       | Assertions with the assert keyword should be used to evaluate invariants' states. | Medium          |                           |              |
| **3.8**     | **Reentrancy**                                               |                 |                           |              |
| 3.8.1       | Ensure that the smart contract state is updated before giving the control execution flow to the external unknown smart contract. | High            |                           |              |
| 3.8.2       | Ensure secure mechanisms are in place to prevent same-function and cross-function reentrancy, such as checks, effects, and interactions principles or Reentrancy solutions. | High            |                           |              |
| 3.8.3       | Special attention should be paid when using to the use of the transfer function of ERC721 and ERC1155 tokens to ensure that the data is updated before the transfer operation | High            |                           |              |
| 3.8.4       | Ensure the transferring assets that delegate the execution flow to other smart contracts is done securely. eg: The ERC721 standard code, which triggers the invocation of the onERC721Received function | High            |                           |              |
| 3.8.5       | Certify functions with protection against Reentrancy attacks are tested for such scenarios. | High            |                           |              |
| **3.9**     | **Exceptions**                                               |                 |                           |              |
| 3.9.1       | Always verify internal and external call return values for unexpected events and define behavior accordingly. | High            |                           |              |
| 3.9.2       | Ensure custom exceptions are created to enhance the exception handling capabilities and code readability. | Medium          |                           |              |
| **3.**10    | **Gas Consumption**                                          |                 |                           |              |
| 3.10.1      | Verify that the Dapp smart contract functions are implemented in a manner that gas consumption persists stable over time. | High            |                           |              |
| 3.10.2      | Always provide enough gas when performing a sub-call to another smart contract. The gas calculation should be justified as it may vary over time. | High            |                           |              |
| **3.11**    | **Denial of Service**                                        |                 |                           |              |
| 3.11.1      | Ensures proper exception management when transferring crypto assets, such as using try-and-catch blocks. | High            |                           |              |
| 3.11.2      | Avoid using unbounded loops or looping over user-defined parameters without proper controls. If so, ensure the logic execution scale over time with the use of the smart contract. | Medium          |                           |              |
| 3.11.3      | Self-destruct usage should be avoided as assets other than infrastructure tokens and funds sent to the contract \ after self-destruction would be lost. Also, smart contract data is not erased from the Blockchain history. Finally, self-destruction is irreversible. If really necessary, its usage should be documented and tested | Low             |                           |              |
| **3.12**    | **Monitoring and Alerting**                                  |                 |                           |              |
| 3.12.1      | Similar to web applications, smart contracts should be monitored as part of the operations of a running decentralized application. | High            |                           |              |
| 3.12.2      | The alerting system should also be implemented to detect and alert teams of unexpected behavior. | High            |                           |              |
| **3.13**    | **Low-Level Calls**                                          |                 |                           |              |
| 3.13.1      | Ensure proper management of errors in low-level calls as they do not raise exceptions. | High            |                           |              |
| 3.13.2      | Smart contracts should properly validate the response of a low-level call response, as it can be manipulated by the called smart contracts. | High            |                           |              |
| 3.13.3      | Avoid using delegatecall low-level calls, only use them if really necessary and only if the target contract is trusted and secure. | Medium          |                           |              |
| **3.14**    | **Upgradeable Contracts**                                    |                 |                           |              |
| 3.14.1      | Ensure the proxy upgradeability has access control and is only actionable with a wallet using a multiple-account solution. | High            |                           |              |
| 3.14.2      | Verify that the proxy and implementation deployment or upgrade process is done in one transaction so that they cannot be front-run. | High            |                           |              |
| 3.14.3      | For initialized implementations, verify that the proxy implementation is initialized. | High            |                           |              |
| 3.14.4      | Certifying the proxy implementation cannot be destroyed. In such a scenario, the proxy contract would not be able to upgrade. | High            |                           |              |
| 3.14.5      | Ensure the upgradeable contract has no overlap between the storage used by the implementation contract and the one used by the proxy. | Medium          |                           |              |
| **3.15**    | **Randomness**                                               |                 |                           |              |
| 3.15.1      | Certify that random numbers are generated in a secure fashion. | High            |                           |              |
| **4**       | ***Architecture\***                                          |                 |                           |              |
| 4.1         | Smart contracts are fundamentally immutable. Ensure that adequate patterns are used to enable smart contract code upgrading over time and in case of incidents. | High            |                           |              |
| 4.2         | Ensure that any ERC standard is implemented correctly, and validated thanks to a wide range of tests. | High            |                           |              |
| 4.3         | For visibility and state tracking, use events to announce state changes or business actions. | High            |                           |              |
| 4.4         | Ensure that at least the critical business flows have their external and internal dependencies clearly documented. Eg: oracles, liquidity pools, and smart contract standards. | Medium          |                           |              |
| 4.5         | If smart contract addresses require being deterministic, use the appropriate low-level call. Low-level calls aren’t recommended and should be used at your own risk. | Low             |                           |              |
| **5**       | ***Access Control\***                                        |                 |                           |              |
| 5.1         | Verify smart contracts' functions' access follow the least privilege principle. | High            |                           |              |
| 5.2         | Ensure that users only have access to smart contracts they are intended to. | High            |                           |              |
| 5.3         | Certification of the access control on the web application side is aligned with the one existing in the smart contract. | High            |                           |              |
| 5.6         | The access control mechanism of a large decentralized application should be centralized for better control. | High            |                           |              |
| 5.7         | Verify the existence of reentrancy protection for functions modifying smart contract state. | High            |                           |              |
| 5.9         | Certify that critical roles in the decentralized application are not managed by a single user. | High            |                           |              |
| 5.10        | The transaction sender should be validated using the correct means only. | High            |                           |              |
| 5.11        | Access control mechanisms should be thoroughly tested according to specifications and free from vulnerabilities. | High            |                           |              |
| 5.12        | When implementing an off-chain authentication mechanism on smart contracts, ensure the implementation follows a standardized and widely tested one. | High            |                           |              |
| 5.13        | Prevent smart contract roles having elevated privileges (such as mint, transfer, change ownership,etc …) to be associated with an External Owner Address (EOA). | High            |                           |              |
| 5.14        | Verify all modifiers' logic are simple and use the correct mechanisms to perform input validation. | High            |                           |              |
| 5.15        | Verify that any change in access control configuration should follow an internal well-defined process. | Medium          |                           |              |
| 5.16        | The access control mechanism of a large decentralized application should be centralized for better control. | Low             |                           |              |
| 5.17        | Describe and document any existing time lock mechanism and its purpose. | Low             |                           |              |
| **6**       | ***Business Logic\***                                        |                 |                           |              |
| 6.1         | Ensure the logic of the smart contract does not assume it cannot receive infrastructure tokens. | Medium          |                           |              |
| 6.2         | **Front Running**                                            |                 |                           |              |
| 6.2.1       | To prevent front-running in a Dapp, and protect users, ensure that one of the following solutions is in place: Preventing time and order to have to influence the outcome of the transaction, using a pre-commit scheme, or limiting the benefits a front-runner could have. | Medium          |                           |              |
| 6.3         | **Denial of Service**                                        |                 |                           |              |
| 6.3.1       | Ensure that Dapp logic cannot be impacted by Dos attacks such as block stuffing, where an attacker prevents other transactions from being validated over a certain period of time. | Medium          |                           |              |
| **7**       | ***Utility Tokens\***                                        |                 |                           |              |
| **7.1**     | **General**                                                  |                 |                           |              |
| 7.1.1       | Tokens need to meet the corresponding specification standards. Use existing standards that have been widely tested. | High            |                           |              |
| 7.1.2       | Project administrators should not have high-authority functions to operate user token assets. | High            |                           |              |
| 7.1.3       | Ensure decentralized applications only request user token approval for the exact amount of tokens the user wants to transfer. | High            |                           |              |
| 7.1.4       | The token handling fee should have a reasonable range, rather than potentially being modified arbitrarily by the administrator. | Medium          |                           |              |
| **7.2**     | **Reflection Token**                                         |                 |                           |              |
| 7.2.1       | Validate that the rate calculation mechanism of the token is done safely. The token handling fee should have a reasonable range, rather than being arbitrarily specified by the administrator. | High            |                           |              |
| **8**       | ***Code Clarity\***                                          |                 |                           |              |
| 8.1         | Certify the developers are using the recent stable version of the compiler. | High            |                           |              |
| 8.2         | Ensure that modifications to pertinent smart contract state variables activate corresponding events and certify their functionality. | Medium          |                           |              |
| 8.3         | All storage variables should be initialized.                 | Medium          |                           |              |
| 8.4         | Clearly define the smart contract variables' location as storage, memory, or calldata. | Medium          |                           |              |
| 8.5         | Verify that the smart contracts code makes the distinction between trusted(owned smart contracts) and untrusted (3rd party) smart contracts. | Medium          |                           |              |
| 8.6         | Certify that assembly low-level code is only used if necessary and is properly commented on and documented. | Low             |                           |              |
| 8.7         | Certify that unchecked code is clearly commented on following industry standards and documented. | Low             |                           |              |
| 8.8         | For the developer's readability, ensure technical documentation in the contract. | Low             |                           |              |
| 8.9         | Avoid using functions and variables with similar names.      | Low             |                           |              |
| 8.10        | Logic should be clear and kept in simple modular contracts and functions. | Low             |                           |              |
| 8.11        | Clean unused variables and functions                         | Low             |                           |              |
| 8.12        | The inheritance order for contracts should be defined and documented to prevent bugs using multiple inheritance or shadow functions. | Low             |                           |              |
| 8.13        | Certifying the code annotation matches the code implementation. | Low             |                           |              |
| 8.14        | Verify that the same rules for variable naming are followed throughout all the contracts (e.g. use the same variable name for the same object). | Low             |                           |              |
| **9**       | ***Education and Training\***                                |                 |                           |              |
| 9.1         | Provide team members with regular training around smart contract security and best practices. | High            |                           |              |
| 9.2         | Maintain internal documentation of best practices to be followed by team members and new joiners. | High            |                           |              |
| 9.3         | Ensure team members are fully aware of phishing, ice phishing, social engineering attacks, and new techniques of scams. | High            |                           |              |