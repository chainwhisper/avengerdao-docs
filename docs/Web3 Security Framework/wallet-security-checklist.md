# Crypto Wallet Security Checklist

Classification: **Restricted**

**Stage: Enquiry stage (40)**

**Introduction**:

The Web3 Security Framework Initiative is a collaborative effort to promote the adoption of best practices in web3 security. The initiative aims to minimize the risks associated with security vulnerabilities and hacks, which have become increasingly prevalent in the web3 space. Moreover, projects that demonstrate full compliance with our rigorous guidelines will earn an on-chain certificate recognized by all the AvengerDAO members on the BNB Chain ecosystem.

This document serves as a comprehensive checklist of the critical elements surrounding the secure management of crypto wallets.

| Item ID | Security Check                                               | Criticality | Is Project Compliant? | Comments |
| ------- | ------------------------------------------------------------ | ----------- | --------------------- | -------- |
| **1**   | **General**                                                  |             |                       |          |
| 1.1     | Define an evolutive policy outlining the organization's approach to securing cryptocurrency wallets that should be communicated to all employees and stakeholders and reviewed and updated regularly. Such a document will contain the measures taken in the elements below. | TBD         |                       |          |
| 1.1.1   | Define the different purposes of the project's wallets used by a project and the amount limit to reduce impact in case of a hack or leak. Eg: wallets for treasury, development and testing purposes, payment, etc. | TBD         |                       |          |
| 1.1.2   | Establish roles and responsibilities associated with managing wallet security topics as in a responsibility matrix. | TBD         |                       |          |
| **2**   | **Education and Training**                                   |             |                       |          |
| 2.1     | Provide team members with regular training around wallet security and best practices. | TBD         |                       |          |
| 2.2     | Maintain internal documentation of best practices to be followed by team members and new joiners. | TBD         |                       |          |
| 2.3     | Ensure team members are fully aware of phishing, ice phishing, and social engineering attacks. | TBD         |                       |          |
| **3**   | **Wallet Software and Hardware Selection**                   |             |                       |          |
| 3.1     | Certify to use a wallet that uses secure/audited cryptographic libraries. | TBD         |                       |          |
| 3.2     | The wallet development team should ensure the secure integration of third-party solutions, this includes creating mechanisms to switch solutions without impacting the business. | TBD         |                       |          |
| 3.3     | Certify the wallet software is continually updated by the team to integrate any security patch. | TBD         |                       |          |
| 3.4     | Certify the wallet solution chosen has been thoroughly audited for security vulnerabilities and that they provide vulnerability remediation in a timely manner. | TBD         |                       |          |
| 3.5     | Hardware wallets should be purchased through formal channels to avoid supply chain attacks. | TBD         |                       |          |
| **4**   | **Operations**                                               |             |                       |          |
| 4.1     | Document and track the list of wallets and their purposes. Avoid using wallets for purposes they were not intended to. | TBD         |                       |          |
| **5**   | **Wallet Sharing**                                           |             |                       |          |
| 5.1     | Define secure processes for sharing wallet information among developers. | TBD         |                       |          |
| **6**   | **Single point of failure**                                  |             |                       |          |
| 6.1     | To reduce the risk associated with stolen or leaked private keys, wallets with funds should use a security solution providing redundancy and access control - such as Smart Contract Wallets (Multi-signature), Multi-party Computation Wallets, and Multi-Factor Authentication (MFA) mechanisms. Note: Multisig wallets and MPC wallets are the preferred solution from a security perspective. | TBD         |                       |          |
| 6.2     | Multisig Wallet threshold should be at least 50% of the total number of owners. | TBD         |                       |          |
| 6.3     | Accounts associated with roles, having elevated privileges in smart contracts should also be assigned to several accounts using a redundant solution such as Smart Contract Wallet (Multi-Signature). | TBD         |                       |          |
| 6.4     | Make sure to implement mechanisms for the redundancy of wallets so that they are not lost in case of unexpected events. | TBD         |                       |          |
| **7**   | **Phishing attacks**                                         |             |                       |          |
| 7.1     | Define guidelines for developers when working with wallets with funds—using a secure environment and tools, such as secure and up-to-date tools, browsers, and usage of only secure extensions to prevent known phishing attacks. | TBD         |                       |          |
| 7.2     | Ensure tools used for development are strictly used for that purpose and have no 3rd party extensions or dependencies unrelated to web3 development. | TBD         |                       |          |
| **8**   | **Development Lifecycle**                                    |             |                       |          |
| 8.1     | Define a list of secure wallet software that can be used by team members and ensure they are used. | TBD         |                       |          |
| 8.2     | Define access control measures, following the principle of least privileges, for team members to use the private keys and access project funds. | TBD         |                       |          |
| 8.3     | Define guidelines for storing private keys encrypted in the local environment. Private keys shouldn’t be stored or shared in plain text. | TBD         |                       |          |
| 8.4     | To prevent indiscriminate usage and manipulation of wallets in an environment not controlled by the project, define the process and access control for users to use wallets in the local environment. | TBD         |                       |          |
| **9**   | **Wallets and Servers**                                      |             |                       |          |
| 9.1     | Use secure solutions to store private keys on test and production servers such as Hardware security modules and Key Management Systems. | TBD         |                       |          |
| 9.2     | Define secure guidelines for storing private keys associated with the production testing environment encrypted on test servers and ensure secure access control. | TBD         |                       |          |
| 9.3     | Certify the usage of at least one different wallet for testing environments and for production environments. | TBD         |                       |          |
| **10**  | **Treasury**                                                 |             |                       |          |
| 10.1    | Implement monitoring and alerting mechanisms to detect moving funds. | TBD         |                       |          |
| 10.2    | Keep track of wallets used for such purposes.                | TBD         |                       |          |
| 10.3    | Create a straightforward process for the management of such wallets, authorized users, process steps, and usage use cases. | TBD         |                       |          |
| 10.4    | Clearly define the standard for secure wallet solutions for treasury wallets for the project combining some of the following solutions: cold wallet solutions or hardware wallets, multisig, and MFA. And Implement it | TBD         |                       |          |
| 10.5    | Create a straightforward procedure for when migrating funds to another wallet, with an internal chain of approval | TBD         |                       |          |
| 10.6    | Create a process for when changing any software or hardware associated with the treasury wallets. | TBD         |                       |          |
| **11**  | **Incident Management**                                      |             |                       |          |
| 11.1    | Create an incident response protocol to secure funds for the different scenarios where private keys are compromised - The process could be different for each type of wallet - Treasury wallets, wallets with elevated roles in smart contracts, etc. | TBD         |                       |          |
| 11.2    | Rehearse the incident response protocol to ensure its effectiveness. | TBD         |                       |          |

