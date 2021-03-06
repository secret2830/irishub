
# IRISnet Validator FAQ

## IRISnet

IRISnet is designed to be the foundation for next generation distributed business applications. It is a BPoS blockchain, built with Cosmos-SDK, that enables cross-chain interoperability through a unified service model.

## IRIShub

**IRIShub** is the first blockchain in IRISnet. It's based on Tendermint Bond-Proof-of-Stake（BPoS）Consensus. One of key innovations of IRIShub is iService. 
IRIShub started its betanet in mid-Feb, read more [here](https://medium.com/irisnet-blog/iris-betanet-is-going-to-launch-11d1bf420b9d)

## IRIS Service

![IRIS网络图](https://github.com/irisnet/irisnet/blob/master/images/chap2-1.png?raw=true)

*IRIS Services* (a.k.a. "iService") are introduced to bridge the gap between the blockchain world and the conventional business application world, mediating the complete lifecycle of off-chain services -- from their definition, binding (provider registration), invocation, to their governance (profiling and arbitration).

## Lifecycle

* **Definition:** Definition of what an off-chain iService can do in terms of an Interface Definition Language (IDL) file.

* **Binding:** Declaration of the location (address), pricing and QoS of a provider endpoint that implements a given iService definition.

* **Invocation:** Handling of consumer requests to and provider responses from a given iService provider endpoint.

## Providers
*Providers* are network users who offer the implementation of one or more iService definitions and often act as *adaptors* of off-chain services and resources located in other public and consortium chains, as well as in enterprise legacy systems.  Providers monitor and process incoming requests and send responses back to the network.  A provider could at the same time act as a consumer by sending requests to other providers.  As planned, providers would be required to charge a fee for any services they might offer, and the service fee, by default, would be priced in the IRIS token.

## Consumers
*Consumers* are those users who consume iService by sending requests to designated provider endpoints and receiving responses from providers in question.

## Profilers
*Profilers* are special consumers who act on behalf of the IRIS Foundation Limited, a Hong Kong incorporated company limited by guarantee that takes the lead in building the IRIS network.  Profilers are the sole users authorized to invoke iServices in the *profiling mode*, which is intended to help create and maintain objective provider profiles that consumers refer to for provider screening.

## Arbitrators
*Arbitrators* are self-declared users who, working collectively, arbitrate consumer complaints against provider performance.  The details about the arbitration mechanism are being actively worked on, please keep an eye on our [whitepaper](../resources/whitepaper-en.md).

## IRISnet Node Types

- **Full Node**
  A full node is a fully functional peer in IRIS network
  - Voting power is 0；
  - Save a full backup of transaction history；
  - Could be upgrade to validator node 
- **Validator Node**
  - Validator node is a staking pool, which is responsible for signing votes to reach consensus, and verify/execute transactions in blocks. It could be seen as miners in PoW blockchains.
  - Participate in on-chain governance, vote for proposals；
  - Upgrade software to latest version
- **Validator Candidate Node**
  At the start of IRISnet, only top 100 bonded full node will become validator nodes, the rest will become candidates. The situation will change as delegation amount changes. 
  - Voting power is 0；
  - No Block provision


## IRIS Token

The IRIS hub has its own native token known as *IRIS*.  It is designed to serve three purposes in the network.

* **Staking.**  Similar to the ATOM token in the Cosmos Hub, the IRIS token will be used as a staking token to secure the PoS blockchain.

* **Transaction Fee.**  The IRIS token will also be used to pay fees for all transactions in the IRIS network.

* **Service Fee.**  It is required that service providers in the IRIS network charge service fees denominated in the IRIS token.

It is intended that the IRIS network will eventually support all whitelisted fee tokens from the Cosmos network, which can be used to pay the transaction fees and service fees.

## IRISnet User Type

###  IRISnet Validator
People that operator validator nodes. They must first stake some tokens with certain transaction and is responsible for maintain the validator nodes
and get rewards in return.
###  IRISnet Delegator
People that cannot, or do not want to run validator operations, can still participate in the staking process as delegators. 
###  IRISnet Profiler
Profiler is a type of user that they are a special type of user who can submit software upgrade/halt proposals
###  IRISnet Trustee
Trustee is a type of user that  they are a special type of user who will receive funds from TxTaxUsage proposals

##  Profit and Loss Analysis for IRISnet Valdiators

###  IRISnet Validators Profit
Validator and its delegators could share the following rewards by portion：
* **Block Proposer Reward**
  In IRIShub, the probability for validators is proportional to its bonded tokens. If one's proposed block is finalized, it gets extra rewards for it.
  
* **Block Provision**
  Block provisions exist to incentivize IRIS holders to stake. As more IRIS tokens are staked, more secure the network become. Read more about [Staking](../features/stake.md) here. 
  Block provision will be [distributed every block](../features/mint.md)。 [Inflation rate](../features/mint.md) in IRISnet for the first year will be 4%.  **This ration could be adjusted by `parameter-change` proposals**。
  In this way, loose IRIS will devalue year by year. 

* **Fee** 
Each transaction needs a [fee](../features/basic-concepts/fee.md#fee) for compensating validators' work[Gas](../features/basic-concepts/fee.md#gas). These fees can be paid with IRIS and later in any tokens which are whitelisted by the Hub’s governance. Fees are distributed to validators in proportion to their stake. A minimum fee/gas ration is set in IRISnet.

Each validator receives revenue in proportion to its total stake. However, before this revenue is distributed to its delegators, the validator can apply a commission for providing staking services. 

###  IRISnet Validators Risks

-   **Unavailability**: Validators are expected to keep signing votes for making new blocks. If a validator’s signature has not been included in more than  half of the last 34,560 blocks (which amounts to approximately 24 hours, assuming an average block-generating time of 5 seconds)，this validator will get jailed and removed from current validatorset for 1 day. 
-   **Double Sign**:If the protocol detects that a validator voted multiple different opinions about the same block (same height/round), or voted for different blocks at the same height/round, this validator will get jailed and removed from current validatorset for 2 days. Their bonded tokens will get slashed by 1%.
-   **Censorship**: If the protocol detects that a proposer included invalid transactions in a block, this validator will get jailed remove from current validatorset for 2 days.

All metrics mentioned could be adjusted by `parameter-change` proposals. 

### Token Management
* Type of IRIS
There are two states of IRIS token: **Loose** and **Bonded**.

Loose tokens could be transferred between two accounts and loose tokens will be bonded if token holders do a [delegate transaction](../cli-client/stake/delegate.md) 
Validator Node's [Voting Power](../features/stake.md)is the sum of tokens delegate by himself and his delegators。
* Bond IRIS
If some delegator wants to withdraw the bonded tokens, he could execute a [unbond](../cli-client/stake/unbond.md) transaction. In IRISnet, the time to wait for bonded IRIS tokens 
become loose is **3 weeks**. This is called `unbonding_period`, which is critical for PoS network security.

* Redelegate IRIS
In each `unbonding_period`, delegator could redelegate his delegations from one validator to another without waiting for 3 weeks.
* Manage IRIS Reward
By staking, you will earn some rewards, these tokens are loose. So, you could trade them anytime.


## How to Become IRISnet Valdiator

Refer to [Running a Validator Node](../get-started/Validator-Node.md)

**Advices**
To earn more delegation for your validator, you are advised to:
 - Undergo a security audit
 - Open-source some dev tools and workflow
 - Setup your own website to build your own image

## IRISnet Ecosystem
**Wallet**
- Rainbow  https://www.rainbow.one
- IRIS TOken：Get some testnet IRIS from [Faucet](https://www.irisnet.org/docs/zh/get-started/Validator-Node.html#%E8%8E%B7%E5%BE%97iris%E4%BB%A3%E5%B8%81)；Once [Betanet](https://www.irisnet.org/mainnet?lang=CN)goes live, an airdrop of tokens is planned. 


**Explorer**
https://www.irisplorer.io

##  IRISnet Testnet and Mainnet

**IRISnet Testnet Fuxi** 

IRISnet testnet is called Fuxi. The Fuxi testnet is used to provide a stable test environment for developers such as third-party wallets, browsers and other applications。 

Learn more: [How to use Testnet](../get-started/Join-the-Testnet.md)

**IRISnet Betanet**

Betanet is the first part of launching IRISnet mainnet. Betanet started at mid-Feb. More news will be available in [IRISnet Official Website](https://www.irisnet.org/mainnet?lang=CN)。 

Learn more: [How to_join_Mainnet](../get-started/Join-the-Mainnet.md)

## Validator Communication Channel

- Riot chat: #irisvalidators:matrix.org
- IRIShub Validator Working Group QQ Group：834063323

