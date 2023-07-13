
# Project Management Best Practices Checklist

Classification: **Restricted**

**Stage: Enquiry stage (40)**

**Introduction**:

The Web3 Security Framework Initiative is a collaborative effort to promote the adoption of best practices in web3 security. The initiative aims to minimize the risks associated with security vulnerabilities and hacks, which have become increasingly prevalent in the web3 space. Moreover, projects that demonstrate full compliance with our rigorous guidelines will earn an on-chain certificate recognized by all the AvengerDAO members on the BNB Chain ecosystem.

This document serves as a comprehensive checklist of the critical elements surrounding the web3 project management best practices.

|           |                                                              |             |                       |          |
| --------- | ------------------------------------------------------------ | ----------- | --------------------- | -------- |
| Item ID   | Security Check                                               | Criticality | Is Project Compliant? | Comments |
| **1**     | **Technology Selection**                                     |             |                       |          |
| 1.1       | Certify the list of solutions the decentralized application is allowed to integrate and keep track of any vulnerability that might be detected. | TBD         |                       |          |
| 1.2       | Ensure the separation of roles of your Web application, most processing, external communication, management of keys, and solution integration should be done in the backend application, leaving the frontend for displaying backend data and managing user interaction and inputs. | TBD         |                       |          |
| 1.3       | Certification of a remediation plan for issues with Infrastructure, oracles, bridges, tech providers, etc. | TBD         |                       |          |
| **2**     | **Development Lifecycle**                                    |             |                       |          |
| **2.1**   | **Design**                                                   |             |                       |          |
| 2.1.1     | Formally define the business case and the technical solution to address the problem to be solved. | TBD         |                       |          |
| **2.2**   | **Development**                                              |             |                       |          |
| 2.2.1     | Ensure there are processes in place to track vulnerabilities in external dependencies. | TBD         |                       |          |
| **2.3**   | **Testing and Validation**                                   |             |                       |          |
| 2.3.1     | Several testing strategies should be in place (unit testing, integration testing, regression testing as well as stress testing), at least for the business-critical scenarios. Such scenarios should be clearly documented and results should be validated in the project development lifecycle before the production release. | TBD         |                       |          |
| 2.3.2     | Stress testing scenarios [non-exhaustive]: Adverse market conditions, Adverse token price fluctuations, Issues with key inputs (eg. oracle pricing going offline, etc.), Edge-case/extreme event situations etc. Assess the impact on the project, other projects, and the overall ecosystem of these stress-testing scenarios. | TBD         |                       |          |
| **2.4**   | **Continuous Integration**                                   |             |                       |          |
| 2.4.1     | Ensure continuous integration pipelines are in place and perform the unit and integration tests. | TBD         |                       |          |
| 2.4.2     | Ensure security tests are also part of the continuous integration process. | TBD         |                       |          |
| **2.5**   | **Deployment**                                               |             |                       |          |
| 2.5.1     | Certify the correctness of the deployment scripts.           | TBD         |                       |          |
| 2.5.2     | Verify smart contracts on blockchain explorers for the specific chain the projects are being deployed. | TBD         |                       |          |
| **2.6**   | **Monitoring**                                               |             |                       |          |
| 2.6.1     | Ensure the capacity of the project to monitor on-chain the project smart contract activity once the deployment is complete. | TBD         |                       |          |
| 2.6.2     | In case of an unexpected event such as funds being siphoned, an alert system should be triggered and the project point of contact should be notified. | TBD         |                       |          |
| **3**     | **Decentralized Application**                                |             |                       |          |
| **3.1**   | **Web2 Stack**                                               |             |                       |          |
| **3.1.1** | **Infrastructure**                                           |             |                       |          |
| 3.1.1.1   | Ensure operations guidelines are in place for infrastructure management and incident response. | TBD         |                       |          |
| 3.1.1.2   | Ensure the implementation of secure infrastructure security best practices. | TBD         |                       |          |
| **3.1.2** | **Network**                                                  |             |                       |          |
| 3.1.2.1   | Ensure network security thanks to firewalls and DDoS attack prevention mechanisms. | TBD         |                       |          |
| **3.1.3** | **Software Security**                                        |             |                       |          |
| 3.1.3.1   | Ensure the security of frontend and backend applications using testing, and static and dynamic code analysis, and are free of any OWASP vulnerabilities. | TBD         |                       |          |
| 3.1.3.2   | Ensure RPC and API endpoints are properly configured and secured, via access control, authorization, and authentication. | TBD         |                       |          |
| **3.1.4** | **Cryptographic Keys Secure Storage**                        |             |                       |          |
| 3.1.4.1   | Use secure means for storing cryptographic keys and seed phrases such as Hardware Security Modules and Key Management Services. | TBD         |                       |          |
| **3.1.5** | **Secured Equipment**                                        |             |                       |          |
| 3.1.5.1   | Establish a policy to guarantee that all personnel utilizes secure devices equipped with essential firewall and antivirus security measures. | TBD         |                       |          |
| **3.2**   | **CVEs and Tech Stack**                                      |             |                       |          |
| 3.2.1     | Implement a procedure for regularly monitoring and addressing new Common Vulnerabilities and Exposures (CVEs) across the entire technology stack. | TBD         |                       |          |
| **3.3**   | **General Security**                                         |             |                       |          |
| 3.3.1     | Establish mechanisms to ensure the protection and maintenance of service availability, confidentiality, and integrity through certifiable means. | TBD         |                       |          |
| **3.4**   | **Risk Management**                                          |             |                       |          |
| 3.4.1     | Put in place a strategy to adhere to established industry standards, such as ISO 27001, NIST Cybersecurity Framework, etc. | TBD         |                       |          |
| **3.5**   | **Transaction signing**                                      |             |                       |          |
| 3.5.1     | To reduce surface attacks on private keys and prevent their leakage, ensure that all project-related transactions and transactions generated for customer custodian wallet are signed offline. | TBD         |                       |          |
| **4**     | **Web3 Stack**                                               |             |                       |          |
| **4.1**   | **Wallet interface**                                         |             |                       |          |
| 4.1.1     | Ensure transactions appear clearly in the user's wallet prior to signing, ensuring readability and transparency, and preventing the signing of undesired transactions. | TBD         |                       |          |
| **5**     | **Training**                                                 |             |                       |          |
| 5.1       | Implement a comprehensive training program to ensure that all personnel is regularly updated on the latest security concepts and best practices. | TBD         |                       |          |
| **6**     | **Audit**                                                    |             |                       |          |
| 6.1       | To enhance the project security maturity, it is recommended to conduct periodic security audits with reputable security firms. | TBD         |                       |          |
| 6.2       | Certify that all audit recommendations are implemented.      | TBD         |                       |          |
| **7**     | **Tokens**                                                   |             |                       |          |
| 7.1       | Implement a mechanism for continuously monitoring the projected liquidity, including the health of DEX liquidity pools and the security of the platforms where the token is traded, to ensure the viability and stability of the token economy. | TBD         |                       |          |
| **8**     | **External Parties**                                         |             |                       |          |
| 8.1       | The list of dependencies of external projects should be clearly documented and updated over time. Eg: wrapped assets, vaults/farms, multi-protocol dependencies, libs (Openzeppelin) oracles (BNB, Chainlink), Dex for liquidity. | TBD         |                       |          |
| 8.2       | Verify there are channels of communication existing with external parties and partners. | TBD         |                       |          |
| 8.3       | Projects should not only rely on notification and communication because of delays, it becomes fundamental they also monitor on-chain dependencies. Partners should be able to provide means to do so. | TBD         |                       |          |
| **9**     | **Change Management**                                        |             |                       |          |
| 9.1       | Establish clear definitions for roles and responsibilities regarding the governance, management, and security of smart contracts, funds, and internal systems to ensure accountability and effective decision-making. | TBD         |                       |          |
| 9.2       | It is common to find unexpected behaviors in a piece of software, and verify the existence of a process to make changes in a timely manner, with the chain of internal validation. | TBD         |                       |          |
| 9.3       | Additionally, establish a tested and reliable process for safely resolving production issues, enabling prompt corrective action to be taken with confidence, and following an internal chain of validation to ensure prompt and effective resolution. | TBD         |                       |          |
| **10**    | **Incident Response**                                        |             |                       |          |
| **10.1**  | **Incident Response for External Causes**                    |             |                       |          |
| 10.1.1    | Verify that channels work both ways and that your project is aware of the means of communication of your external partner in case they suffer from an incident. | TBD         |                       |          |
| 10.1.2    | Certify that remediation protocols are in place in case external partners suffer severe business impact. eg: hack. | TBD         |                       |          |
| **10.2**  | **Incident Response for Internal Causes**                    |             |                       |          |
| 10.2.1    | Ensure that partners with critical dependencies are aware of your security processes and if they have to participate in the project's incident response activity. | TBD         |                       |          |
| 10.2.2    | Certify that internal teams and external dependencies have rehearsed incident response protocols, where they perform their expected role. | TBD         |                       |          |
| 10.2.3    | It recommends projects that have the means to stop an attack and fix the issue without impacting the business. | TBD         |                       |          |
| **10.3**  | **Communication**                                            |             |                       |          |
| 10.3.1    | Ensure the existence of dedicated channels to communicate with the community and partners about unexpected events in a timely manner. | TBD         |                       |          |
| **11**    | **Post Incident**                                            |             |                       |          |
| 11.1      | Certify the existence of a process for the establishment of a post-mortem following major unexpected events such as hacks, service unavailability, etc. | TBD         |                       |          |