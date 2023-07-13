---
sidebar_position: 4
---
# Specification

## BSC Security Detail

**Basic information**, token, address, creator, holding address and other basic information, whether it has been blacklisted maliciously, whether it has been reported to participate in fraudulent money laundering crimes, etc.

**Permission Control**, contracts can be upgraded and modified logic, contract creators have excessive permissions, core parameters can be adjusted at will, unlimited additional issuance and other permissions issues.

**Code Vulnerabilities**, refer to swcregistry for various pure code-level code vulnerabilities, such as computational overflow, lack of authentication, and reentrancy attacks.

**Business Logic Vulnerabilities**, high handling fees, and business-level malicious logic such as restrictions on buying and selling.

| Name                                      | Risk Type                      | Risk Level  | Risk Desc                                                    |
| ----------------------------------------- | ------------------------------ | ----------- | ------------------------------------------------------------ |
| unverified_sourcecode                     | code vulnerabilities           | MEDIUM_RISK | The contract has not verified sourcecode                     |
| high_tax                                  | business logic vulnerabilities | LOW_RISK    | Buy or sell tax too high for this token                      |
| is_exploiter_address                      | basic information              | HIGH_RISK   | This address has been reported to participate in fraudulent exploits. |
| is_flashloan_exploiter_address            | basic information              | HIGH_RISK   | This address has been reported to participate in fraudulent flashloan attacks. |
| Malicious Address                         | basic information              | HIGH_RISK   | Address directly involved in malicious events, Example: DeFi protocol exploiters, centralized exchange hackers, sanctioned addresses, etc. |
| Suspected Malicious Address               | basic information              | MEDIUM_RISK | Address associated with malicious events                     |
| High-risk Tag Address                     | basic information              | LOW_RISK    | High-risk entity address, Example: Mixers, some nested exchanges, etc. |
| Medium-risk Tag Address                   | basic information              | LOW_RISK    | Medium-risk entity address, Example: Gambling, exchanges not requiring KYC, etc. |
| Risk Exchange                             | basic information              | LOW_RISK    | Exchanges that do not require KYC, etc.                      |
| Interact With Malicious Address           | basic information              | MEDIUM_RISK | Interactions with malicious address                          |
| Interact With Suspected Malicious Address | basic information              | LOW_RISK    | Interactions with suspected malicious address                |
| Interact With High-risk Tag Address       | basic information              | LOW_RISK    | Interactions with high-risk address                          |
| Interact With Medium-risk Tag Addresses   | basic information              | LOW_RISK    | Interactions with medium-risk address                        |
| is_gambling                               | basic information              | LOW_RISK    | Address associated with gambling activities                  |
| is_theft                                  | basic information              | HIGH_RISK   | Address associated with theft                                |
| is_trojan                                 | code vulnerabilities           | HIGH_RISK   | Address associated with Trojan attacks                       |
| is_piracy                                 | basic information              | MEDIUM_RISK | Address associated with piracy                               |
| is_associated_address_of_sanction         | basic information              | HIGH_RISK   | Address associated with sanctioned entities                  |
| is_child_abuse_material                   | basic information              | HIGH_RISK   | Address associated with child abuse material                 |
| is_nft                                    | basic information              | BASE_INFO   | Address associated with non-fungible tokens                  |
| is_gamefi             | basic information              | BASE_INFO    | Address associated with GameFi (gaming and finance)          |
| is_cross_bridge       | basic information              | BASE_INFO    | Address associated with cross-chain bridges                  |
| is_web3               | basic information              | BASE_INFO    | Address associated with Web3 applications                    |
| is_mining_pools       | basic information              | LOW_TRUST    | Address associated with mining pools                         |
| is_btc_service        | basic information              | LOW_TRUST    | Address associated with Bitcoin services                     |
| is_exchange           | permission control             | MEDIUM_TRUST | Address associated with cryptocurrency exchanges             |
| is_deposit            | permission control             | MEDIUM_TRUST | Address associated with deposit services                     |
| is_custodian          | permission control             | MEDIUM_TRUST | Address associated with custodian services                   |
| is_atm                | basic information              | MEDIUM_TRUST | Address associated with crypto ATMs                          |
| is_entity             | basic information              | BASE_INFO    | Address associated with a known entity                       |
| anti_whale_modifiable | business logic vulnerabilities | MEDIUM_RISK  | It describes whether the contract has the function to modify the maximum amount of transactions or the maximum token position |
| hacker                | basic information              | BASE_INFO    | Whether or not the token is associated with a hacker         |
| scam                  | business logic vulnerabilities | BASE_INFO    | An attempt to defraud users by promising them something of value that is not real |
| malware               | basic information              | BASE_INFO    | Whether or not the token is associated with malware          |
| sanction              | basic information              | BASE_INFO    | Whether or not the token is subject to any sanctions         |
| blackmail             | basic information              | BASE_INFO    | Whether or not the token is involved in any blackmail activities |
| bot                   | basic information              | BASE_INFO    | Whether or not the token is associated with a bot            |
| ransomware            | basic information              | BASE_INFO    | Whether or not the token is associated with ransomware       |
| darknet               | basic information              | BASE_INFO    | Whether or not the token is associated with a darknet        |
| whale                 | permission control             | BASE_INFO    | This refers to an entity or individual that holds a large amount of cryptocurrency or digital assets on a blockchain, potentially giving them significant influence over the network |
| exchange                    | basic information              | BASE_INFO   | Whether or not the token is associated with an exchange      |
| miner                       | basic information              | BASE_INFO   | Whether or not the token is associated with a miner          |
| dapp                        | basic information              | BASE_INFO   | Whether or not the token is associated with a decentralized application (DApp) |
| terrorism                   | basic information              | BASE_INFO   | Whether or not the token is associated with terrorism        |
| pass-through                | business logic vulnerabilities | BASE_INFO   | A vulnerability that allows an attacker to transfer funds from one address to another without the owner's knowledge |
| wallet                      | basic information              | BASE_INFO   | Whether or not the token is associated with a wallet         |
| contract                    | permission control             | BASE_INFO   | Whether a particular address is a smart contract             |
| defi                        | business logic vulnerabilities | BASE_INFO   | Decentralized finance (DeFi) is a form of finance that enables users to interact with digital assets, such as cryptocurrencies, without the need for a central authority |
| unaffiliated                | basic information              | BASE_INFO   | A security risk where a transaction or asset is not associated with any known or trusted entity or user |
| token                       | basic information              | BASE_INFO   | Whether a particular address is a token                      |
| Vulnerability               | code vulnerabilities           | BASE_INFO   | Security vulnerabilities in smart contracts can be exploited to steal funds |
| Overpowered role            | permission control             | BASE_INFO   | The ability to assign an overpowered role to an address can be used to manipulate the blockchain data |
| Not using default libraries | code vulnerabilities           | BASE_INFO   | Not using default libraries can lead to security vulnerabilities |
| Overpowered owner           | permission control             | BASE_INFO   | This refers to a situation where a single individual or entity has too much power or control over a blockchain network, potentially leading to centralization and increased risk of fraud or manipulation |
| Gas consumption             | business logic vulnerabilities | BASE_INFO   | The amount of computing power needed to execute a transaction on a blockchain network |
| Rugpull                     | business logic vulnerabilities | HIGH_RISK   | A scam where the creator of a project abandons it after collecting a large amount of funds from investors |
| Code quality                | code vulnerabilities           | BASE_INFO   | Poor code quality can lead to security vulnerabilities       |
| Optimization                | code vulnerabilities           | BASE_INFO   | Poorly optimized code can lead to security vulnerabilities   |
| Documentation issues        | basic information              | LOW_TRUST   | Whether or not there are any documentation issues associated with the token |
| Design drawback             | business logic vulnerabilities | MEDIUM_RISK | An issue with the design of a blockchain that can lead to security vulnerabilities |
| DeFi integration issues               | business logic vulnerabilities | MEDIUM_RISK  | Issues that can arise when integrating DeFi protocols with other systems |
| is_access_control                     | permission control             | LOW_RISK     | The owner or deployer has too much control over the contract. Make sure the deployer is trustworthy before interacting with such contracts. |
| is_attacker_related                   | basic information              | HIGH_RISK    | The address is related to an attacker.                       |
| is_compromised                        | basic information              | HIGH_RISK    | The address's private key is leaked or compromised.          |
| is_not_open_source                    | basic information              | MEDIUM_RISK  | The contract is not open source. Interact with unverified contracts carefully. |
| is_risky                              | basic information              | HIGH_RISK    | The contract contains one or more risks that might influence users' funds. Interacting with a risky contract is not recommended. |
| is_vulnerable                         | code vulnerabilities           | HIGH_RISK    | The contract contains exploitable vulnerabilities. Interacting with vulnerable contracts is not recommended. |
| mixer                                 | basic information              | BASE_INFO    | Whether or not the token is mixing funds                     |
| number_of_malicious_contracts_created | basic information              | BASE_INFO    | The total number of malicious contracts created by the token |
| address-zero                          | code vulnerabilities           | MEDIUM_RISK  | Risk associated with a blockchain-based system that has an address with zero tokens. |
| constant-condition                    | code vulnerabilities           | MEDIUM_RISK  | Risk associated with a constant condition in a contract that can be exploited |
| controlled-external-call              | code vulnerabilities           | HIGH_RISK    | A vulnerability that allows an attacker to call external functions on a blockchain and control their execution |
| internal-function-exposed             | code vulnerabilities           | HIGH_RISK    | A vulnerability that allows an attacker to access internal functions on a blockchain |
| router-modifiable                     | code vulnerabilities           | MEDIUM_RISK  | A vulnerability that allows an attacker to modify the routing of traffic on a blockchain |
| staking-pools                         | code vulnerabilities           | MEDIUM_TRUST | Grouping of users who pool their resources together to increase their chances of getting rewards |
| timelock                              | code vulnerabilities           | BASE_INFO    | Timelock features can be abused to delay transactions or manipulate blockchain data |
| verified                              | basic information              | HIGH_RISK    | Whether or not the token has been verified                   |
| wrong-direction                       | code vulnerabilities           | LOW_RISK     | Transactions can be sent in the wrong direction and can lead to losses |
| swc-107-eth                           | code vulnerabilities           | HIGH_RISK    | This is a security vulnerability in the Ethereum network, which allows a malicious user to steal funds |
| abandon                               | basic information              | LOW_RISK     | Whether or not the token has been abandoned by its creators  |
| buyers-and-sellers    | basic information              | MEDIUM_RISK | buyers and sellers of the token                              |
| deposit-fee           | basic information              | MEDIUM_RISK | The fee for depositing the token                             |
| emission-rate         | basic information              | MEDIUM_RISK | The rate at which new tokens are issued                      |
| hardhat-buy-sell-fees | basic information              | LOW_RISK    | The fees for buying/selling the token using the Hardhat platform |
| liquidity             | basic information              | MEDIUM_RISK | The token's liquidity                                        |
| token-holders         | basic information              | MEDIUM_RISK | The total number of token holders                            |
| tornado               | business logic vulnerabilities | MEDIUM_RISK | A tornado is a malicious attack on a blockchain network that allows the attacker to steal funds and disrupt the network. |
| limit-tx-count        | basic information              | LOW_RISK    | The total number of transactions limited by the token        |
| modify-fee            | basic information              | MEDIUM_RISK | Whether or not the token's fee structure can be modified     |
| fake_token_cache      | basic information              | MEDIUM_RISK | The total number of fake tokens in the token's cache         |
| is_in_blist           | permission control             | HIGH_RISK   | Checking if an address is in a blacklist                     |
| cars_risk_score       | basic information              | HIGH_RISK   |                                                              |
| trust_list            | basic information              | HIGH_TRUST  | It describes whether the token is a famous and trustworthy one |
| is_open_source        | basic information              | HIGH_RISK   | Un-open-sourced contracts may hide various unknown mechanisms and are extremely risky. |
| proxy_contract        | permission control             | LOW_RISK    | A smart contract that acts as an intermediary between other smart contracts on a blockchain network. It can introduce additional risks if there are bugs or vulnerabilities in the proxy contract code |
| is_mintable           | permission control             | LOW_RISK    | Risk associated with a blockchain-based system that allows for minting of additional tokens |
| owner_address         | basic information              | LOW_TRUST   | The address of the token's owner                             |
| take_back_ownership   | permission control             | BASE_INFO   | The ability to take back ownership of a contract can be used to steal funds or manipulate the blockchain data |
| modifiable_balance    | permission control             | BASE_INFO   | The ability to modify the balance of a contract can be used to manipulate the blockchain data |
| owner_change_balance  | permission control             | HIGH_RISK   | It describes whether the contract owner has the authority to change the balance of any token holder |

## Reference documentation

https://owasp.org/ A non-profit foundation dedicated to improving software security, not only blockchain security, providing various conferences and training, and you need to pay to join.

https://swcregistry.io/ is about contract code security vulnerabilities. Similar to a static compiler, it only focuses on code quality and contract vulnerabilities , and provides various attack cases.

https://docs.gopluslabs.io/reference/token-security-api-response-detail/contract-security Go+ Security Audit Provider

https://www.certik.com/projects/binance certik security vendor

https://ave.ai/check Decentralized exchange detection

https://bscscan.com/tokens bsc has a total of about 2.7 million BEP-20 tokens, more than 40,000 ERC-721 and more than 4,000 ERC-1155 NFTs.

https://tokensniffer.com/ Token sniffer, to detect the basic information of the code and information related to liquidity

https://ethereum.org/en/developers/docs/standards/ ERC Specifications

https://blog.csdn.net/sanqima/article/details/120863024Address type, Externally Owned Accounts, referred to as EOA, it has a private key; Contract Account, referred to as CA, has no private key;

Address classification: The current classification is basically based on the ERC specification. ERC uses mostly tokens and NFTs. Others that do not follow the specification can be classified as custom dApps, and in addition to contracts, there will also be Security check of individual user address EOA. Therefore, the current classifications include Token, NFT, dApp, and EOA.