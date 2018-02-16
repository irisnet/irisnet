# IRIS Network
**Inter-chain service infrastructure and protocol for building trustworthy and distributed business applications**

Harriet Cao harriet@bianjie.ai

Haifeng Xi haifeng@bianjie.ai
Harriet Cao harriet@irisnet.org<br/>
Haifeng Xi haifeng@irisnet.org

_NOTE: If you can read this on GitHub, then we're still actively developing this
document.  Please check regularly for updates!_

## Table of Contents ###########################################################

* [IRIS Overview](#iris-overview)
  * [Cosmos and Tendermint](#cosmos-and-tendermint)
  * [New Innovations from IRIS](#new-innovations-from-iris)
* [IRIS Network Design](#iris-network-design)
  * [Network Actors](#network-actors)
  * [IRIS Services](#iris-services)
  * [IBC Enhancement](#ibc-enhancement)
* [Use Cases](#use-cases)
* [Token Economics](#token-economics)
* [Fundraiser](#fundraiser)
* [Roadmap](#roadmap)
* [The Team](#the-team)
* [Core Members](#core-members)
* [Advisors](#advisors)
* [References](#references)

<div STYLE="page-break-after: always;"></div>

## Disclaimer

This whitepaper and any other documents published in association with this whitepaper relate to the intended development and use of the IRIS network.  They are information purposes only and may be subject to change.

* This whitepaper describes a developing project

This whitepaper contains forward-looking statements that are based on the beliefs of IRIS Foundation Limited, as well as certain assumptions made by and information available to IRIS Foundation Limited.  

The IRIS network as envisaged in this whitepaper is under development and is being constantly updated, including but not limited to key governance and technical features. The IRIS token involves and relates to the development and use of experimental platforms (software) and technologies that may not come to fruition or achieve the objectives specified in this whitepaper.

If and when the IRIS network is completed, it may differ significantly from the network set out in this whitepaper. No representation or warranty is given as to the achievement or reasonableness of any plans, future projections or prospects and nothing in this document is or should be relied upon as a promise or representation as to the future.

* No offer of regulated products

The IRIS tokens are not intended to represent a security or any other regulated product in any jurisdiction.

This document does not constitute an offer or solicitation of securities or any other regulated product, nor a promotion, invitation or solicitation for investment purposes. The terms of the purchase are not intended to be a financial service offering document or a prospectus of any sort.

The IRIS tokens do not represent equity, shares, units, royalties or rights to capital, profit, returns or income in the platform or software or in IRIS Foundation Limited or any other company or intellectual property associated with the platform or any other public or private enterprise, corporation, foundation or other entity in any jurisdiction. 

* This whitepaper is not advice

This whitepaper does not constitute advice to purchase any IRIS tokens. It must not be relied upon in connection with any contract or purchasing decision.

* Risk warning

The purchase of IRIS tokens and participation in the IRIS network carries with it significant risks. 

Prior to purchasing IRIS tokens, you should carefully assess and take into account the risks, including those listed on <https://www.irisnet.org/> and in any other documentation. 

* Views of IRIS Foundation Limited only

The views and opinions expressed in this whitepaper are those of IRIS Foundation Limited and do not necessarily reflect the official policy or position of any government, quasi-government, authority or public body (including but not limited to any regulatory body of any jurisdiction) in any jurisdiction.  

Information contained in this whitepaper is based on sources considered reliable by IRIS Foundation Limited but there is no assurance as to their accuracy or completeness.   

* English is the authorised language of this whitepaper

This whitepaper and related materials are issued in English only. Any translation is for reference purposes only and is not certified by IRIS Foundation Limited or any other person. No assurance can be made as to the accuracy and completeness of any translations. If there is any inconsistency between a translation and the English version of this whitepaper, the English version prevails.

* No third party affiliation or endorsements

References in this whitepaper to specific companies and platforms are for illustrative purposes only. The use of any company and/or platform names and trademarks does not imply any affiliation with, or endorsement by, any of those parties.

* You must obtain all necessary professional advice

You must consult a lawyer, accountant and/or tax professional, as well as any other professional advisors, as necessary prior to determining whether to purchase IRIS tokens or otherwise participate in the IRIS network.

<div STYLE="page-break-after: always;"></div>


## IRIS OVERVIEW ################################################################

> IRIS network is named after the Greek goddess of the Rainbow who is the
> faithful messenger between heaven and mortals.

Contractual relationships are a fundamental building block of human society and the
importance of blockchain technology lies in providing a very efficient
and cost effective way of realizing reliable contractual
relationships. For the first time, trust is not needed (which is also very
costly to establish) when multiple parties participate in sophisticated
business interactions. It has been said that blockchain technology provides
the most important elements for distributed business to take place: lifting network effect
and very low transaction cost. More and more people see the potential of
blockchains as the new internet of value and will gradually transform the
current business models into more efficient distributed ones. Especially
the token mechanism embedded in most modern blockchain emphasizes each network
participant's right and will disrupt business in its current form [\[1\]][1].

However, blockchain technology is still in its infancy with drawbacks
such as poor or limited performance and immature governance mechanisms,
making it unfit to support real-world distributed business
applications. Consortium chains such as Hyperledger Fabric, R3 Corda, or
Ethereum Enterprise are trying to address the performance and governance
issues in order to make blockchain technology more suitable for business
collaboration. However, today consortium chains are dominated by huge
enterprise companies. Furthermore their close-form off on-chain governance model
is very inefficient. Without a token economics model and the
openness and the excitement in public chains, the consortium chains lack
vitality. We would like to enhance the current blockchain technology and
make it possible to enable thousands and millions of SMBs and even
individual freelance business service providers to provide their
services and enjoy the rewards in an open network. To achieve this goal,
we have identified the following challenges/opportunities for technology
innovations:

* Not all computation could or should be implemented as on-chain computations such as smart contracts

The [Turing-complete](https://en.wikipedia.org/wiki/Turing_completeness) virtual
machine provided by Ethereum [\[2\]][2] runs Smart Contracts gives people a lot of hope of developing
decentralized applications. However Smart contracts can only handle deterministic logic (so
every node can reach an identical state after processing every
transaction and block) while huge amount of existing business logic that
is not deterministic and might vary at different time and under
different environmental parameters. Especially these days, business
systems have been using more and more computer algorithms（NLP, machine
learning, operation research algorithms）for decision optimization. In
algorithms, very often we purposely add some randomness to make the
decision not to get stuck at local optimal states while trying to find a
better sub-optimal result.

On the other hand, some of the real world business logics are meant to
be run once off-chain and shouldn't be implemented as smart contracts
this type of replicated computing.

**Integration and collaboration of off-chain services and resources with
a distributed ledger is key to further advance the adoption of
blockchain technology for more real-world use scenarios.**

* How to reuse the existing blockchain resources? : both public chains and consortium chains

It is infeasible to use one public chain addressing all the problems.
Every day there are different chains going live which focus on one aspect
of problem solving such as distributed storage, predict market etc.
According to the coinmarketcap.com, there are more than 1000
cryptocurrencies currently active on various exchanges.

While building business applications involve handling storage and also
different source of data feeds. Another motivation of our work involves
how to support building distributed business applications by reusing
some of the existing work like storage (IPFS, SIA, Storj.io etc.), data feed
(Augur, Gnosis, Oraclize etc.) and IoT (IOTA etc.) provided by those
dedicated blockchains and not reinventing the wheel.

Besides, there are many (near) real-time business transactions do need
more close form consortium/permission/private chains to address
performance, security and business governance requirements.

**Our vision of distributed business infrastructure needs to have the Interoperability of many heterogeneous chains including public/consortium/ permission/private chains.**

Inter-chain technology is a very nature answer to the requirement.
However, till today, the existing Inter-chain technologies are mainly
designed to provide interoperability among existing blockchains and
focus on token value transfer. The question of how to consume the
resource provided in different chains still remains unanswered.

Comparing the proposed inter-chain technologies like Cosmos [\[3\]][3] and
Polkadot [\[4\]][4], we find out that Cosmos provides more mature base for
interoperability and scalability. Especially, we found the design of
"`many hubs and many zones`" and "`each zones are independent blockchains
having independent governance models`" from Cosmos provides a very
suitable architecture for modeling the real world complexity in a SOC
way. To best reuse the existing framework, we present the IRIS Network, a
decentralized inter-chain network composing hub and zones with
implementing a layer of service infrastructure based on
Cosmos/Tendermint [\[5\]][5], with enhanced usage of token .

Since our work is built on top of Cosmos/Tendermint, we will overview
Cosmos/Tendermint to set the stage, summarize the features we inherit
from Cosmos/Tendermint and the innovations we are building on top of
existing work.

### Cosmos and Tendermint ################################################################

Cosmos \[3\] is an ambitious project aiming at building the internet
of blockchain. It is a network of many independent blockchains, called
zones. Each zone is powered by classical Byzantine fault-tolerant (BFT)
consensus protocols like [Tendermint](https://tendermint.com/).

Tendermint provides a high-performance, consistent, secure BFT consensus
engine, where strict fork-accountability guarantees hold over the
behavior of malicious actors. Tendermint is well suited for scaling
heterogeneous blockchains including public blockchains such as Ethermint
[\[6\]][6], which is a blazing fast Proof-of-Stake implementation of
Ethereum, as well as performance critical permission/consortium chains.
The successful stories on using Tendermint in the permission/consortium
chain domain including Oracle [\[7\]][7], CITA [\[8\]][8] and
Hyperledger Burrow [\[9\]][9].

Tendermint is used as the consensus protocol for building the first zone
on Cosmos Hub. Hub can connect to many different
kinds of zones, and the communication is achieved via an
inter-blockchain communication (IBC) protocol, a kind of virtual UDP or
TCP for blockchains. Tokens can be transferred from one zone to another
securely through the Cosmos Hub, without the need for an exchange
or a trusted third party between zones.

To develop robust interoperable blockchains and blockchain applications
with Cosmos Hub, Cosmos SDK provides blockchain development
\'starter-kit\' of common blockchain modules while not enforcing
user stories thus giving maximum flexibility for application customization.

### New Innovations from IRIS ################################################################

IRIS network aims to build technology foundation which facilitate
construction of distributed business applications. It goes beyond today's
blockchain systems which are mainly for digitalized assets.

The key challenges we are addressing in IRIS are two parts:
* Integration and collaboration of off-chain computing and resources on
  a distributed ledger;
* interoperability of the services across
  heterogeneous chains.

We address those challenges through incorporation
of a service oriented infrastructure into Cosmos/Tendermint which is
called `iService`.

The design of iService inherits the  thinking pattern from
many years' SOA practices. SOA is an architectural approach to create
systems built from autonomous services which have explicit boundaries,
share schema and contract [\[13\]][13]. Earlier practice of SOA focus
on implementation of Enterprise Service Bus (ESB) which enables
communication among services via a common communication bus which
consists of a variety of point-to-point connections between providers
and consumers. Centralized management of services through ESB could
trigger a single point of failure, also adds dependency of service
deployment. The recent surge of Micro-services Architectural Style can be
seen as a development of SOA without focusing on ESB rather using
light message queues for inter service communication. In IRIS network,
the inter service communication is implemented over blockchain to
leverage blockchain as a trusted machine for mediating business
collaborations. It runs without prerequisite of existing trust among service
provider and service consumer which is very hard to establish.

IRIS network use Tendermint protocol as a high-performance consensus
engine. Leveraging the flexibility provided by tendermint's Application
BlockChain Interface (ABCI), we define a set of service infrastructure
transaction types including service provisioning, service consumption
and service governance. As explained earlier, most business logic is not
suitable for implementation as deterministic smart contracts on
blockchain, we are using this service layer to move the business
application specific logics and transaction processing off the
blockchain itself and use the blockchain only to get consensus on the
results generated through those services. This idea is also inspired by
existing work from blockchain community when address performance issues
of moving some complicated computation off the main chain, such as Lightning
Network's off-chain state channels [\[10\]][10] as well as Plasma's fraud
proof side chains [\[11\]][11]. Although we are not implementing side chains,
we rip traditional business logic computation off the blockchain
 and use it as a trustworthy mediation bus for
complicated business collaboration.

For inter chain communication, Cosmos IBC [\[12\]][12] defines a protocol for
transferring values from an account on one chain to an account on the
other chain. IRIS  designe new semantics to allow cross
chain computation to be invoked by leveraging IBC. This capability is very important when
building scalable business applications. More on its use
case is in later chapter.

IRIS network provides the service infrastructure for handing the
coordination of on-chain transaction processing with off-chain data
processing and business logic execution. The `iServices` also have defined
protocols for them to be invoked cross chain if required. IRIS also provides
client-side tools including smart wallet for inter-chain multi-asset as well as for accessing `iServices`.
IRIS project plans to provide SDKs for easy construction of `iServices`.
For example, for a specific service definition, SDKs are provided for generating the
service provider side skeleton as well as service consumer side stub for
major languages.


## IRIS Network Design ################################################################

![Figure of IRIS Network](https://github.com/irisnet/iris-community/blob/query/pics/chap2.png?raw=true)

Being part of the Cosmos ecosystem, IRIS network builds on top of
the Tendermint & Cosmos technology stack by introducing a comprehensive
service infrastructure and enhanced IBC processing.

As illustrated in figure above, IRIS network has the same topology as
Cosmos network, with IRIS Hub itself being connected to the
Cosmos Hub as one of IRIS zones. IRIS full nodes are developed with
IRIS-SDK, which extends Cosmos-SDK with a service infrastructure and
integrates with an embeded IPFS node.

IRIS Services (a.k.a. `iServices`) bridge the gap between blockchain
world and conventional business application world, mediating a
complete lifecycle of off-chain services -- from their definition,
binding (provider registration), invocation, to their governance
(profiling and dispute resolution). By enhancing the IBC processing
logic to support service semantics, IRIS-SDK allows distributed business
services to be available across the internet of blockchains.

Although the IRIS network focus on providing an innovative solution
for distributed business applications, it is still part of
the broader Cosmos network. All zones connected to the IRIS hub can
interact with any other zone in the Cosmos network over the standard IBC
protocol. In fact, by introducing a layer of service semantics and thus
enabling a whole new set of business scenarios, the IRIS network helps
to increase the scalability and diversity of the Cosmos network, to increase
value transfer volume through the Cosmos hub, and to increase the
overall value of the network.

### Network Actors

1. **Consumers** are users who consume off-chain services by sending
  requests to and receiving responses from the network.

2. **Providers** offer implementation of one or more `iService` definitions
  and often act as *adaptors* of off-chain services and resources located
  in other public and consortium chains as well as enterprise legacy
  systems. They monitor and process incoming requests and send responses
  back to the network. A provider could at the same time act as a consumer
  by sending requests to other providers. Providers will charge a fee for
  any services they might offer, and the service fee, by default, is
  priced in the IRIS network's native fee token known as `*iGas*`; providers
  could also price their services in other whitelisted Cosmos fee tokens
  such as photon \[?\].

3. **Profiler** is a special user working on behalf of the IRIS Foundation,
  a Hong Kong based nonprofit organization in charge of building and
  promoting the IRIS network. Profiler is the sole user authorized to
  invoke iServices in the profiling mode, which helps to create and
  maintain objective *provider profiles* that become handy for consumers
  when it comes to selecting the right providers (see ?).

### IRIS Services

**Service Definition**

A Method is composed of:

* `ID (int)`: The unique ID of this method in the encompassing iService

* `Name (string)`: The unique name of this method in the iService

* `Description (string)`: A description of this method

* `Input (string)`: A structured definition of the input parameters

* `Output (string)`: A structured definition of the output result

* `Error (string)`: A structured definition of all possible error conditions

* `OutputPrivacy (enum)`: Can be one of NoPrivacy or PubKeyEncryption

A ServiceDefinition is composed of:

* `Name (string)`: The name of this iService

* `Description (string)`: A description of this iService

* `Tags (string)`: Comma separated keywords about this iService

* `Creator (string)`: A self-description of the iService creator. *Optional*

* `ChainID (string)`: The ID of the blockchain where this iService was
  originally defined

* `Messaging (enum)`: Can be one of Unicast or Multicast

* `Methods ([]Method)`: The definition of methods available in this
  `iService`

A CreateServiceDefinitionTx transaction is composed of:

* `Definition (ServiceDefinition)`: The service definition to be created

**Service Binding**:

A CreateServiceBindingTx transaction is composed of:

* `DefinitionHash ([]byte)`: The hash of the service definition that the
  provider is binding to

* `ChainID (string)`: The ID of the blockchain where the provider is
  connected

* `ProviderAddress ([]byte)`: The provider's blockchain address

* `BindingType (enum)`: Can be one of Local or Global; choose Global if a
  provider wants the binding to be exposed to the rest of the world;
  otherwise, use Local

* `ProviderDeposit (int64)`: To create an effective binding, the provider
  must put down a deposit (in terms of iGas amount) that is greater than
  the value of the system parameter MinProviderDeposit; a larger deposit
  may imply more trustworthiness of the provider

* `ServicePricing (string)`: A structured definition of the service pricing
  model on a per method basis, including cost per call, volume discount,
  promotional terms etc.; service fee is by default listed in iGas but
  could also be quoted in other whitelisted fee tokens.

* `ServiceLevel (string)`: A structured definition of service level the
  provider agrees to bind himself to, in terms of response time,
  availability etc.

* `BindingExpiration (int64)`: The blockchain height where this binding
  expires; a negative number means "never expire"

An UpdateServiceBindingTx transaction is composed of:

* `DefinitionHash ([]byte)`: The hash of the service definition the
  provider has bound to

* `ChainID (string)`: The ID of the blockchain where the provider is
  connected

* `ProviderAddress ([]byte)`: The provider's blockchain address

* `ChangeSet (string)`: A structured definition of desired changes to an
  existing binding identified by the preceding three fields

A provider can update ServicePricing, ServiceLevel and BindingExpiration
at any time, but a small amount of his deposit will be slashed for
changing the latter two (specified by `ServiceLevelUpdateSlash` and
`BindingExpirationUpdateSlash` respectively). Setting BindingExpiration to
a height that is lower than the current height will be interpreted as
invalidating the binding immediately.

Updates to `ProviderDeposit` will always be treated as *adding to* the
current deposit balance. Whenever the balance drops below
`MinProviderDeposit`, the binding will be disabled until the provider
increases the balance above the threshold. Upon expiration or
invalidation of a binding, the provider will automatically get back the
remaining balance of its deposit.

`BindingType` can be changed from Local to Global, but not the other way
around. To downgrade a binding from Global to Local, a provider must
first invalidate the binding in question and then create a new Local
binding.

If a provider somehow needs to move the binding to a new address, it is
not allowed to update ProviderAddress directly; instead, the provider
should invalidate the current binding and create another one with the
desired new `ProviderAddress`.

Upon successful execution of these two transactions by the application
(i.e., `iService` business logic in the IRIS-SDK), a ServiceBinding object
will be created or updated accordingly.

A ServiceBinding is composed of:

* `DefinitionHash ([]byte)`

* `ChainID (string)`

* `ProviderAddress ([]byte)`

* `ServiceLevel (string)`

* `ServicePricing (string)`

* `BindingExpiration (int64)`

* `IsValid (enum)`: Can be one of True or False

![Figure of IRIS Service](https://github.com/irisnet/iris-community/blob/query/pics/chap2-2.png?raw=true)


**Service Invocation**

Consumers and providers interact with each other through `*endpoints*`.
There are two kinds of endpoints -- `*request table*` and `*response table*`
(see Figure above). Service requests are posted to request tables monitored
by interested provider(s) which pick up and process requests addressed
to them; service results (or errors) are posted back to response tables
monitored in turn by matched consumers.

For a Multicast service, all of its bindings share one request table;
for a Unicast service, however, a separate request table is created and
maintained for each of its bindings. As for the other direction, a
dedicated response table will be created and managed for each consumer.

A ServiceRequest is composed of:

* `ChainID (string)`: The ID of the blockchain where the consumer is
  connected

* `ConsumerAddress ([]byte)`: The blockchain address of the consumer

* `DefinitionHash ([]byte)`: The hash of the service definition

* `MethodID (int)`: The ID of the method to be invoked

* `InputValue (string)`: A structured representation of input values

* `BindingHash ([]byte)`: The hash of the target binding, in case of a
  Unicast service. *Optional*

* `MaxServiceFee (int64)`: The max amount of service fee the consumer is
  willing to pay for a Multicast request. *Optional*

* `Timeout (int)`: The max number of blocks the consumer is willing to wait
  for response(s) to come back

A PostServiceRequestTx transaction is composed of:

* `Requests ([]ServiceRequest)`: The service requests to be posted

* `RequestDeposits ([]int64)`: The consumer must put down for each request
  a deposit (in terms of iGas amount) that is greater than the value of
  MinRequestDeposit; a larger deposit may imply more sincerity of the
  consumer

The application will verify that the requests are coming from a consumer
with matching ChainID and ConsumerAddress, the targeted bindings are
valid, request deposits are sufficient, consumer's account balance is
enough to cover the request deposits and service fees, and that the
number of requests in the transaction is less than MaxRequestPostBatch.

When a verified request is appended to the request table, the related
service fee (MaxServiceFee in case of a Multicast request) will be
deducted from the consumer's account and locked up in escrow.

A GetServiceRequest query is composed of:

* `DefinitionHash ([]byte)`: The hash of the service definition

* `BindingHash ([]byte)`: The hash of this provider's binding to the
  service in question; the application will verify that the binding is
  valid and the caller matches the binding's ChainID and ProviderAddress

* `BeginHeight (uint64)`: The blockchain height from where the application
  should start to retrieve requests for the provider, up to a total number
  that is the lesser of BatchSize and MaxRequestGetBatch

* `BatchSize (int)`: The max number of requests to be returned

A ServiceResponse is composed of:

* `RequestHash ([]byte)`: The hash of the matched request

* `BindingHash ([]byte)`: The hash of this provider's service binding

* `OutputValue ([]byte)`: A structured (potentially encrypted)
  representation of output result. *Optional*

* `ErrorMsg (string)`: A structured representation of error messages.
  *Optional*

A PostServiceResponseTx transaction is composed of:

* `Responses ([]ServiceResponse)`: The service responses to be posted

The application will verify that the responses are coming from a
provider with matching `ChainID` and `ProviderAddress`, and that the number
of responses in the transaction is less than MaxResponsePostBatch. A
verified request will be appended to the response table for the intended
consumer.

A GetServiceResponse query is composed of:

* `RequestHash ([]byte)`: The hash of the original request; the
  application will verify that the caller matches the request's ChainID
  and ConsumerAddress

* `BeginHeight (uint64)`: The blockchain height from where the application
  should start to retrieve responses for the consumer, up to a total
  number that is the lesser of `BatchSize` and `MaxResponseGetBatch`

* `BatchSize (int)`: The max number of responses to be returned

A ConfirmServiceResponseTx transaction is composed of:

* `ResponseHash ([][]byte)`: The hash of responses to be confirmed

The application will verify that the responses to be confirmed are
indeed for a request originated by the caller, and that the number of
responses in the transaction is less than `MaxResponseConfirmBatch`.

Responses that fall out of the Timeout window (and, in case of Multicast
responses, when `MaxServiceFee` runs out as more responses come back) will
not be accepted by the application. A consumer starts processing a
Unicast response immediately upon receiving it. However, for Multicast
responses, a consumer will wait until the Timeout window elapses before
starting to process all responses received, if any.

When a Unicast response is confirmed by the consumer, the associated
service fee will be released from escrow to the matched provider account
-- after a small tax (defined by ServiceFeeTaxRate) is deducted and
added to the *system reserve*; and the associated request deposit will
be returned to the consumer as well.

In case of a Multicast request, the situation is a bit more complex:
when a response is confirmed, only part of the request deposit is
returned to the consumer, in proportion to the response related service
fee vs MaxServiceFee; and after all responses are confirmed, the
remaining escrow balance for the request will be returned to the
consumer.

If a request timeouts without seeing any response come back, the
application will refund the associated escrow balance and request
deposit, in full, back to the consumer. However, if the consumer does
not confirm a response in time (before ResponseConfirmTimeout +
blockchain height of the response), a small penalty (defined by
`ResponseConfirmDelayPenaltyRate`) will be applied before the request
deposit is refunded to the consumer, while the associated service fee
will be released to the provider as usual.

(A summary of the nice things about the design, especially the service
invocation process, would be added later...)

![Figure of Multicast Service](https://github.com/irisnet/iris-community/blob/query/pics/chap2-3.png?raw=true)


**Dispute Resolution**

When a consumer is not satisfied with some service response, there needs
to be a mechanism in place for him to issue a complaint to the provider,
who in turn has an opportunity to present a resolution. Due to the lack
of central authorities in a decentralized world, the dispute resolution
mechanism cannot rely on third party arbitration, and should avoid
introducing subjective evaluation -- which could be abused
by either side. The blockchain faithfully records what happened and let
the facts speak for themselves.

The process to resolve a dispute is very much like that of service
invocation, except that a consumer sends a `Complaint` to the provider,
and the provider responds with a Resolution; and the interactions happen
through a pair of global endpoints known as `*complaint table*` and
`*resolution table*`.

A consumer deposit is required for filing a complaint, and a penalty
will be deducted from this deposit if the consumer does not confirm a
Resolution in time. Similarly, a provider's deposit will be partially
slashed if he fails to respond to a complaint in a timely manner.

A Complaint is composed of:

* `ResponseHash ([]byte)`: The hash of the response in dispute

* `Problem (string)`: A description of the problem with the service response

* `PreferredDisposal (enum)`: Can be one of Refund or Redo

A Resolution is composed of:

* `ComplaintHash ([]byte)`: The hash of the matched complaint

* `Disposal (enum)`: Can be one of Refund or Redo

* `Refund (uint64)`: Service fee refund. *Optional*

* `OutputValue ([]byte)`: A structured (potentially encrypted)
  representation of output result. *Optional*

**Service Profiling**

Bootstrapping the `iService` ecosystem presents a few challenges, one of
which is how to make it easy for consumers to find the right providers.
This is a chicken-and-egg problem: consumers need performance metrics to
evaluate and select a provider, yet without consumer usage no
performance metrics will be available.

Here we introduce a profiling mechanism where a privileged system user,
known as `Profiler`, invokes all the active services on a regular
schedule, leaving objective performance traces in the network (such as
response time, availability, complaint handling etc.) that are useful
for real consumers.

Service profiling calls are exempt from service fees and consumer
deposits, but they do incur network transaction fees. These calls
originate from a few reserved addresses that are recognized and honored
by the application.

Profiling activities stay at a relatively stable level for new services
and will gradually wind down for individual services as they start to
attract real consumer calls and thus generate more performance data on
their own.

Profiling cost will be paid out from the system reserve by default, and
the IRIS Foundation reserve will step in if necessary.

**Query**

All the service related lifecycle objects described above can be queried
using the ABCI Query interface (Ref?). These queries are executed over
the Query connection and do not participate in the consensus process. We
have already seen how GetServiceRequest and GetServiceResponse queries
work as part of the service invocation process.

Below is a (not exhaustive) summary of supported queries:

**Service Objects**


| **Object**                               | **Commonly Used Filters**                | **Authorization**                        |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| Service Definition                       | Name, keywords, source (chain id), messaging type, with active bindings... | Anyone can query                         |
| Service Binding (for a given definition) | Location (local or remote), pricing, service level, expiration... | Anyone can query                         |
| Service Request                          | Service definition and binding, blockchain height, batch size | Service definition and binding, blockchain height, batch size |
| Service Response                         | Service request, blockchain height, batch size | Only matched consumer                    |


**Performance Metrics**


| **Area**                    | **Metrics**                              | **Authorization** |
| --------------------------- | ---------------------------------------- | ----------------- |
| Provider (address)          | Number of services provided (ever and active), active time, requests served (local and remote), requests missed, complaints received, complaints missed, ... | Anyone can query  |
| Provider (binding)          | Active time, requests served (local and remote), requests missed, complaints received, complaints missed, ... | Anyone can query  |
| Consumer (address)          | Number of services ever used, requests made, requests confirmed (in time and missed), complaints made, resolutions confirmed, ... | Anyone can query  |
| Consumer (service, binding) | Requests made, requests confirmed (in time and missed), complaints made, resolutions confirmed, ... | Anyone can query  |


### IBC Enhancement

One unique advantage of establishing our service infrastructure on top
of Cosmos is to allow services to be *deployed once and invoked
everywhere*, over an internet of blockchains. Specifically, we need to
accomplish the following:

1. Service definitions are broadcast to every zone in the IRIS network;

2. Global service bindings are broadcast to every zone in the IRIS network;

3. Service requests or complaints targeting a remote provider are routed to
  the blockchain where the provider is connected;

4. Service responses or resolution meant for a remote consumer are routed
  back to the blockchain where the consumer is connected.

When processing a `CreateServiceDefinitionTx` transaction, the application
first validates and stores `ServiceDefinition` locally, and then creates
an `IBCPacket` containing the definition for each neighboring chain. Each
neighbor eventually receives -- from the corresponding relay process --
an `IBCPacketTx` containing the packet, if the definition does not already
exist in the receiving chain, the latter will pass on the definition by
creating an `IBCPacket` for each of *its* neighbors -- except the source
chain from which it received the packet in the first place; if the
definition already exists, the receiving chain stops passing on the
definition.

Similarly, when a `ServiceBinding` is created or updated with its
BindingType set or updated to Global, an IBCPacket containing the
binding is created for each neighboring chain, and gets propagated to
the whole IRIS network.

An `IBCPacket` described above is composed of:

* `Header (IBCPacketHeader)`: The packet header

* `Payload (ServiceDefinition or ServiceBinding)`: The bytes of the service
  definition or binding

The `IBCPacketHeader` above is composed of:

* `SrcChainID (string)`: The ID of the blockchain creating this packet

* `DstChainID (string)`: The ID of the neighboring blockchain this packet is
  destined for

* `Number (int)`: A unique number for all packets

* `Status (enum): NoAck`

* `Type (string): "iris-service-definition" or "iris-service-binding"`

Now let's look at how interchain service invocation happens through IBC.
When a request is made for a Unicast service, the application checks if
the target binding is local, if so, the ServiceRequest is appended to
the corresponding request table as explained in 2.2; otherwise, an
IBCPacket containing the ServiceRequest will be created instead.

An IBCPacket containing a ServiceRequest is composed of:

* `Header (IBCPacketHeader)`: The packet header

* `Payload (ServiceRequest)`: The bytes of the service request

The IBCPacketHeader above is composed of:

* `SrcChainID (string)`: The ID of the blockchain creating this packet

* `DstChainID (string)`: The ID of the blockchain where the remote provider
  is located, i.e., ServiceRequest.ServiceBinding.ChainID

* `Number (int)`: A unique number for all packets

* `Status (enum)`: AckPending

* `Type (string)`: "iris-service-request"

* `MaxHeight (int)`: Current height + ServiceRequest.Timeout

As a remote request finally arrives at the destination chain, the
application will append it to the corresponding endpoint (request table)
for the targeted binding. A response to this remote request will be
wrapped in a receipt IBCPacket that is routed all the way back to the
source chain and appended to the remote endpoint (response table) for
the originating consumer.

Request for a remote Multicast service is treated in the same way except
that more than one `IBCPacket` could be generated in the source chain.
Remote complaints and resolutions work exactly like requests and
responses, and therefore will not be elaborated here.

Below is a complete list of application-dependent `IBCPacket` types:

| **Type**                  | **iService Object** |
| ------------------------- | ------------------- |
| "iris-service-definition" | ServiceDefinition   |
| "iris-service-binding"    | ServiceBinding      |
| "iris-service-request"    | ServiceRequest      |
| "iris-service-response"   | ServiceResponse     |
| "iris-complaint"          | Complaint           |
| "iris-resolution"         | Resolution          |


## Use Cases ################################################################

### Distributed AI for privacy preserving data analysis

The proposed service infrastructure has been prototyped by Bianjie AI, a
Shanghai based startup, into its permission product `BEAN (Blockchain
Edge Analytics Network)` to solve the longstanding challenge of getting
data for running analytics models. Although homomorphic encryption is
one of the methods which allows computing to be done over encrypted
data, due to its impractical for solving real world machine learning
problems, BEAN took a different route which is borrowing the idea of
model parallelism from the traditional distributed AI study [\[14\]][14] and
utilizing SOA design patterns in developing distributed analytics
services over blockchain.

To protect data access, the (partial) model that runs on the data side
needs to be open sourced to the client and specified in the service
definition. Since only partial model is released to the client, the
model developer doesn\'t have to worry about someone stealing his/her
idea; on the other hand, the data owner never needs to worry about their
data leaving the premises and thus losing control of its usage. Other
benefits include:
1. only a small amount of parametric data is
  exchanged on blockchain providing a lot of performance gain;
2. providing a more practical way for data usage auditing, which is often
  needed in the healthcare domain.

Healthcare data is high private and security requirements put great
challenge for it being used for cross organization collaboration, such
as cross hospital clinic records search for diagnosis assistance, new
drug clinic test patient identification, health insurance automatic
claim process etc. This MVP service layer implementation is built on top
of `Ethermint` for connecting hospitals, insurance companies as well as
analytics service providers in providing privacy preserving healthcare
data analytics capability. Smart contracts have been implemented to
support on-chain service registration and invocation. One example of the
off-chain data processing is to support DRGs (Diagnosis Related Group)
grouping analytics service. When hospital user invokes DRGs service, the
raw medical record is processed off-chain using service provider
provided client side NLP(implemented as SQL and Python) code stub to
exact structured data inputs for receiving DRGs service over blockchain
without passing the highly confidential raw medical records. The `BEAN`
scenario demonstrated a most complicated service use case including
implementing distributed analytics, and connecting service providers as
well as service consumers, utilizing blockchain to provide audible
transaction ledge as well as trustworthy distributed computing
foundation.

### Data and analytics e-marketplace

We have studied many proposed AI+Blockchain projects. Most of the
projects are mainly targeting to provide data exchange markets as well
as analytics API markets. With proposed `IRIS` infrastructure, those
networks can be built with ease through publishing data as data services
and wrapping analytics API as analytics services utilizing the `IRIS`
service provider SDK.

### Distributed e-commerce

With proposed `IRIS` infrastructure, integration with traditional systems
like `ERP` to get inventory info, or inter-chain query on trusted data
sources on getting information like transportation and weather will be
quite similar way as many enterprise application developers are already
familiar with. With those services integrated to support distributed
e-commerce applications, it is possible for distributed e-commerce
applications to provide similar user experience as the centralized
systems such as Amazon, Alibaba provides.

### Public chain & consortium chain hybrid system

For many business scenario, taking a hybrid architecture of combining
the good features from both public chain and consortium chain can
provide performance, security as well as economic incentives. For
example, hospitals and insurance companies can form consortium
blockchain when supporting high performance medical insurance claim
transactions, while exposing certain information such as the statistics
of certain diseases occurrence as global service which can be invoked
from other public chains. The received fee can be awarded back to
those information providers in the consortium chain, which motivate the
system participants to improve and promote services. With the
infrastructure provided by `IRIS` to efficient support a hybrid system
architecture, large-scale spontaneous collaboration is made possible
while still support the performance and security requirements needed
from many business applications.

There are many use cases can be supported by the `IRIS` service
infrastructure, such as more efficient asset based security systems,
distributed regulation technology such as due diligence, mutual aid
marketplace etc. One of `IRIS` project plans is also working closely with
such application project teams to support and enable them with needed
blockchain infrastructure and allow them to focus on delivering the
envisioned business value more efficiently.

## Token Economics ################################################################

Same as Cosmos Network, the IRIS network also supports a multi-token
model. Besides the tokens held by zone themselves and can be moved from
one zone to another via Hub. There are two types of tokens supporting
IRIS Network's operation:
* staking token **IRIS**
* fee token **iGas**

### IRIS staking token

Taking the same staking mechanism design of Cosmos [\[15\]][15], IRIS Hub has
its own special native token for staking which is called IRIS. IRIS will
be used in following ways:

* Stakes deposited by validators to be eligible to validate transactions
  and commit new blocks

* Non-validator lent out RIS to any validator to earn a share of their
  block fees and rewards

* Voting power to participate in IRIS network governance

Additional inflationary IRIS and block transaction fees are rewarded to
validators and delegators who delegate to validators. The inflation rate
will be carefully designed to encourage the bounding of sufficient IRIS token
to safeguard the network. The yearly inflation rate (a number between
7% and 20%) is dynamically adjusted to support a convergence of 2/3 IRIS
in circulation will be bonded as staking token.

### IRIS fee token

There are two types of fee token in IRIS network:
* **Network fee** token is for spam-prevention and payment to validators in maintaining the
  ledger;
* **Service fee** token is used for payment to service providers
  who deploys iServices and a default payment service token is called
  `iGas`.

IRIS Network will support all the whitelisted fee tokens from
Cosmos plus IRIS staking token as well as iGas. The benefit for
separating fee token from staking token is explained in [\[16\]][16].

Supporting variety of whitelisted fee tokens is a very innovative design
from Cosmos and it provides better experience for both validators as well
as users. In Cosmos, for `network fee token`, each validator has a config
file defines his personal weighting of how much they value each fee
token. Validator can run a separate cron job to update the config file
based on validator preferred live market data or maybe just use a
default config value.

For the `service fee token` design, similarly multi-token model is
supported, the service provider has the freedom to charge the service
through his preferred token on whitelist or simply using the `iGas`.
Generation of `iGas` will help bootstrapping the service binding and
consumption. When service provider binds a service, `iGas` deposits need
to be escrowed. The deposit might be slashed as punishment if service
provider conducts bad behaviors. Detailed design of `iGas` token economics
will be released in future technical yellow papers.

To help IRIS network validators and service providers to mitigating the
crypto-currency price volatility, IRIS foundation plans to facilitate
the deployment of global iServices for retrieving market data from
different exchanges or introducing oracles. Those market data iServices
can be conveniently used by validators as well as service providers to
define the weights in config file as well as adjusting the `iGas` amount
for the bonded services.

Tax, % from all fees (Haifeng ?)

## Fundraiser ################################################################

On Genesis, the initial token supply will be 2,000,000,000 IRIS, and they will
be distributed as follows:

* **Pre-Sale**: 20%

* **ATOM Holders**: 5% (detailed airdrop plan will be announced after
  Cosmos Hub goes alive)

* **Core Developer Team**: 15% (locked up for 6 months starting from IRIS Hub
  launch, and linear monthly release for 2 years afterwards)

* **IRIS Foundation**: 15% (staff and advisor compensation, PoS staking, and
  service profiling etc.)

* **Ecosystem Empowerment**: 45% (bestowal to potential users, swap with
  zones connecting to IRIS Hub, and contigency reserve)

After the IRIS network is fully deployed, the annual inflation rate is
expected to be between 7%\~20% which is adjusted to motivate about 2/3
IRIS tokens in circulation to be bonded for staking. This
inflation will be paid to bonded validators and delegators for
safeguarding the network.

Funds raised will be used for the development and promotion of IRIS network
and for the ongoing expenses required to sustain the growth of the community.
The planned usage is as follows:

* **Software Development**: 40%

* **Community Building**: 20% (meetups and online engagement, developer enablement, and academic sponsorship)

* **Marketing**: 10%

* **Professional Services**: 5% (legal, accounting and auditing)

* **Contingency**: 25%

## Roadmap ################################################################

The IRIS project roadmap includes the following milestones:

* **PANGU** (January 2018 \~ June 2018) As the first stage of the IRIS
  project, we will focus on having the IRIS Hub up and running as one of
  the earliest regional hubs that connect to the Cosmos Hub; we'll get a
  couple of public blockchains to connect to the IRIS Hub as "zones", and
  release an initial version of the mobile client for the IRIS Network.

* **NUWA** (July 2018 \~ November 2018) The is the stage where we will
  build out the fundamental IRIS Service Layer: upgrade the network to
  enable service definition, binding, invocation and query; have a beta
  version of the IRIS SDK ready for developers and upgrade the mobile
  client to support IRIS Services; form strategic alliances with service
  providers and have more zones connected the IRIS Hub.

* **KUAFU** (December 2018 \~ May 2019) Upgrade the network to support
  advanced IRIS Service governance features, such as profiling and dispute
  resolution; keep improving the SDK and mobile client; rapidly expand the
  network to connect with more zones and integrate more service providers.

* **HOUYI** (Beyond June 2019) Move toward the realization of a
  distributed business ecosystem, through relentless technology
  innovations, effective community building and sustained developer
  empowerment.

## The Team ################################################################

**Tendermint** (the team building Cosmos), **Wancloud**(a subsidiary of Wanxiang
Blockchain) and **Bianjie AI** will team together to build IRIS
infrastructure. Tendermint is going to give technical advice/development
support to IRIS project in extending Tendermint ABCI and Cosmos IBC
(inter blockchain communication). Wancloud will be the key strategy
partner to Cosmos/IRIS ecosystems when participating in Cosmos/IRIS
business development in Asia.

**Bianjie AI** will be the core development team for IRIS project
leveraging experience established from building distributed AI analytics
services for healthcare data analysis and exchange.  Bianjie AI is a
Shanghai based startup established in 2016 and focuses on developing
innovative products and solutions for healthcare and financial
industries, using advanced Blockchain and AI technologies. One of
Bianjie's core products `BEAN (Blockchain Edge Analytics Network)` is a
permission chain which delivers distributed data analytics services for
privacy preserving healthcare data analysis and exchange using nature
language processing and machine learning technologies. Bianjie AI is
currently extending `BEAN` capabilities to build IRIS -- a public
inter-blockchain network for distributed business ecosystems. **Bianjie AI**
is also the operation and service partner of Cosmos Network in China.

### Core Members

**Harriet Cao**

Founder of Bianjie AI, which a shanghai based startup focusing on
building smart services for Blockchain that enable trustworthy and
efficient business collaborations using distributed AI technology.
Harriet is an award-winning practitioner of data analytics and
artificial intelligence technologies, and was the recipient of 2010
INFORMS Daniel H. Wagner Prize. Prior to the startup, Harriet worked for
IBM Research for more than 16 years in various capacities including
Director of IBM Research Shanghai Lab and Big Data Analytics Leader for
IBM Global Labs. Harriet has a M.S degree on Robotics from Carnegie
Mellon University and M.S. degree on Automation Control from Tsinghua
University.

**Haifeng Xi**

Mr. Haifeng Xi is a senior technologist and entrepreneur. Since
returning to China from the United States in 2009, he had worked in the
capacity of Chief Technology Officer for three companies, one of them is
NASDAQ listed and the other one is a domestic conglomerate. He also
co-founded two startups in Shanghai, where he plays an active role of
technical leader and engineering champion. Haifeng has a Master's degree
in Electrical and Computer Engineering from the University of Maryland,
and a Master's and Bachelor's degree in Automatic Control from Tsinghua
University.

**Jae Kwon**

After graduating from Cornell in 2005 with an undergraduate degree in
computer science, Jae worked as a software developer in Silicon Valley,
first at Alexa/Amazon, then later at Yelp, where he led their mobile app
development team. After getting the Bitcoin bug, Jae created the
Tendermint BFT consensus algorithm and Tendermint Core blockchain engine
to create a provably secure proof-of-stake algorithm, an alternative to
proof-of-work mining. In addition to Tendermint, Jae is also the creator
of Cosmos, the network of blockchains.

**Tom Tao**

Since joining Wanxiang in August 2016. Tom Tao is responsible for
Wanxiang Blcokchain Consulting service, WanCloud Baas Platform as well
as ChainBase accelerator and incubator service. Before Wanxiang, he had
already accumulated rich practical experience in service management and
business management for over 18 years in global leading companies. With
sharp and forward-looking insight, he introduced industry-leading cloud
service, IoT data service platform, creative accelerator technology and
business into Chinese market. He started tracking the trend of
blockchain, cloud computing, IoT and smart manufacturing industry since
2013, and explored the application scenarios relating to these
Leading-edge technologies. Tom has a Master's degree in Physics from
Fudan University and a Bachelor's degree in Electronic Engineering from
Nankai University.

### Advisors

Jim Yang

Zaki Manian

Adrian Brink

Michael Yuan

## References ################################################################

[1]: https://drive.google.com/file/d/1bI7JIOe-CfJ5fPHKxYlFub2Kg-KCGU6r/view?usp=sharing
[2]: http://ethdocs.org/en/latest/
[3]: https://cosmos.network/whitepaper
[4]: https://polkadot.io/
[5]: https://tendermint.readthedocs.io/en/master/
[6]: https://ethermint.zone/
[7]: http://www.freepatentsonline.com/y2017/0236120.html
[8]: https://github.com/cryptape/cita-whitepaper/blob/master/en/technical-whitepaper.md
[9]: https://github.com/hyperledger/burrow
[10]: https://lightning.network/lightning-network-paper.pdf
[11]:  https://www.plasma.io/plasma.pdf
[12]: https://github.com/cosmos/ibc/blob/master/README.md
[15]: https://medium.com/@tendermint/b5b2c682a292
[16]: https://drive.google.com/file/d/1jtyYtx7t1xy9gxEi2T5lXFNd8xUY7bhJ/view


* [1] Wanxiang Blochchain Inc., Distributed Business Value Research Institute,
  "Blockchain and Distributed Business Whitepaper", September 2017.

* [2] Ethereum Foundation, "Ethereum Homestead Documentation",
  http://ethdocs.org/en/latest/

* [3] Jae Kwon, Ethan Buchman，"Cosmos, A Network of Distributed
  Ledgers", https://cosmos.network/whitepaper

* [4] Gavin Wood, "Polkadot: Vision For a Heterogeneous Muilti-chain
  Framework", https://polkadot.io/

* [5] Tendermint, https://tendermint.readthedocs.io/en/master/

* [6] Ethermint, https://ethermint.zone/

* [7]  Oracle International Corporation, "Accountability and Trust in
  Distributed Ledger Systems", USA Patent Application 20170236120, August
  17, 2017, http://www.freepatentsonline.com/y2017/0236120.html

* [8] Jan Xie, "CITA Technical Whitepaper",
  https://github.com/cryptape/cita-whitepaper/blob/master/en/technical-whitepaper.md

* [9] Hyperledger Burrow, https://github.com/hyperledger/burrow

* [10] Joseph Poon, Thaddeus Dryja, "The Bitcoin Lightning Network:
  Scalable Off-Chain Instant Payments", January 14, 2016,
  https://lightning.network/lightning-network-paper.pdf

* [11] Joseph Poon, Vitalik Buterin, "Plasma: Scalable Autonomous Smart
  Contracts", August 11, 2017, https://www.plasma.io/plasma.pdf

* [12] Ethan Frey, "Cosmos IBC Specification", Sep. 29, 2017,
  https://github.com/cosmos/ibc/blob/master/README.md

* [13] Thomas Erl,  "SOA: Principles of Service Design", Prentice Hall;
  1st edition (July 28, 2007)

* [14] Dean, J., Corrado, G.S., Monga, R., et al, Ng, A. Y. "Large Scale
  Distributed Deep Networks". In Proceedings of the Neural Information
  Processing Systems (NIPS'12) (Lake Tahoe, Nevada, United States,
  December 3--6, 2012). Curran Associates, Inc, 57 Morehouse Lane, Red
  Hook, NY, 2013, 1223-1232.

* [15] Tendermint Blog, "Cosmos Validator Economics -- Revenue Streams",
  January 2018, https://medium.com/@tendermint/b5b2c682a292

* [16] Sunny Aggarwal, "Cosmos Token Model", December 2017,
  https://drive.google.com/file/d/1jtyYtx7t1xy9gxEi2T5lXFNd8xUY7bhJ/view
