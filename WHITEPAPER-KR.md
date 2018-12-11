# IRIS Network 백서
**신뢰가능한 분산화 비즈니스 애플리케이션을 위한 인터체인 서비스 인프라 프로토콜.**

Haifeng Xi haifeng@bianjie.ai<br/>
Harriet Cao harriet@bianjie.ai

_NOTE: 원문 백서는 GitHub에 쓰여져 있으며 내용이 활발하게 업데이트되고 있습니다. 정기적으로 업데이트를 확인하십시오!_
<div STYLE="page-break-after: always;"></div>

## Table of Contents ###########################################################

* [Disclaimer](#disclaimer)
* [IRIS Overview](#iris-overview)
  * [Cosmos and Tendermint](#cosmos-and-tendermint)
  * [IRIS Innovations](#iris-innovations)
* [IRIS Network Design](#iris-network-design)
  * [Network Actors](#network-actors)
  * [IRIS Services](#iris-services)
  * [IBC Enhancement](#ibc-enhancement)
* [Use Cases](#use-cases)
* [Token Economics](#token-economics)
* [Initial Token Distribution](#initial-token-distribution)
* [Roadmap](#roadmap)
* [The Team](#the-team)
  * [Core Members](#core-members)
  * [Advisors](#advisors)
* [References](#references)

<div STYLE="page-break-after: always;"></div>

## 주의사항

해당 백서와 그 외에 관련된 문서는 아이리스 네트워크 개발의 진행 상황의 방향을 제시하는 문서입니다. 해당 문서는 정보 제공 용도로만 작성되었으며, 추후 내용이 변경될 수 있다는점을 인지하시기 바랍니다.

### 이 백서는 개발이 진행되고 있는 프로젝트를 설명하는 문서입니다

이 백서는 아이리스 재단(IRIS Foundation Limited) 미래지향적인 목표를 기반으로 작성되었습니다. 백서에 포함되어 있는 일부 정보는 아이리스 재단이 가진 정보와 일부 추정하는 사항에 대한 내용이 포함되어 있습니다.

해당 백서에서 설명하고 있는 아이리스 네트워크는 꾸준하게 개발되고 있는 상태이며, 이에 따라 거버넌스, 기술적 스펙 등의 일부 내용이 반영되지 않거나 변경될 수 있습니다. 아이리스 토큰은 실험적인 요소가 있는 플랫폼에서 이용되는 토큰입니다. 해당 플랫폼은 이 백서에 따라서 개발되지 않을 수 있습니다.

만약 아이리스 네트워크가 완성될 경우, 이 백서에서 설명한 네트워크의 형태와 매우 다른 형태로 완성될 수 있습니다. 이 백서의 내용은 미래 계획, 일정, 목표 등을 보장하지는 않습니다.


### 비규제 상품에 대한 안내

아이리스 토큰은 그 어떤 국가에서도 증권 또는 규제된 상품을 대체할 용도로 만들어지지 않았습니다. 해당 문서는 증권의 유사수신행위의 용도로 작성된 것이 아니며, 투자 권유, 홍보, 추천 등의 목적이 있지 않습니다. 이 문서는 금융안내서가 아닙니다. 아이리스 토큰은 아이리스 플랫폼과 그 외의 기업, 재단, 등의 지분, 증권, 주식, 로열티, 수익배분 등의 목적으로 제공되는 상품이 아닙니다. 

### 백서는 투자 권유가 아닙니다

이 백서는 아이리스 토큰 투자에 대한 안내가 아닙니다. 백서는 그 어떤 계약 또는 투자 결정의 참고서로 이용될 수 없습니다

### 위험성에 대한 안내

아이리스 토큰을 구매하는 행위와 아이리스 네트워크에 참여하는 것은 위험한 행위일 수 있습니다. 아이리스 토큰을 구매하기 전, 개인은 [아이리스 웹사이트]<https://www.irisnet.org/>에 공지되어있는 경고 외의 모든 리스크를 분석할 의무가 있습니다.

### 이 문서는 오직 아이리스 재단의 입장을 대변합니다

이 문서에 나열된 입장, 의견 등은 오직 아이리스 재단의 것이며 그 어떤 정부의 정부, 준-정부, 기관 등의 입장이 포함되어있지 않습니다. 이 문서에 포함되어 있는 정보는 아이리스 재단의 판단 하에 신뢰성 있는 출처를 기반으로 작성되었지만, 특정 정보의 정확성과 완결성을 보장하지 않습니다.

### 아이리스가 제공하는 백서의 원본은 영어로만 작성되었습니다

이 백서의 원본은 영문으로 작성되었습니다. 이 번역본을 포함한 그 어떤 번역본은 아이리스 재단의 검증을 거치지 않은 사본임을 명시합니다. 아이리스 재단은 특정 번역본의 정확성과 완결성을 보장하지 않습니다. 만약 번역본과 원본의 차이가 있을 경우, 영문 원본이 제공하는 정보가 우위를 가집니다.


### 제3자 연관성과 후원은 없습니다

이 백서에 포함되어있는 레퍼런스들은 오직 예시를 목적으로 포함되었습니다. 특정 회사, 플랫폼 명칭 그리고 상표는 해당 기관의 후원, 연관성 또는 협력 관계를 뜻하지 않습니다.

### 전문적인 의견에 대한 공지

아이리스 토큰을 구매하거나 아이리스 네트워크에 참여하기 전에, 개인은 본인의 변호사, 세무사, 회계사 등 해당 분야의 전문가의 의견을 구해야 합니다.

<div STYLE="page-break-after: always;"></div>

## 아이리스  개요 ################################################################

> 아이리스 네트워크는 그리스 신화에서 무지개의 화신이자 천국과 인간 사이의 충실한 메신저인‘아이리스’신에서 유래합니다.

계약 관계(contractual relationship)는 인간 사회의 근본적인 요소 중 하나이다. 블록체인의 중요성은 바로 계약 관계를  합리적인 비용에 효율적으로 제공한다는 것에서 시작된다.

비즈니스 환경에서 개인 간 또는 기관 간 신뢰를 쌓기 위해서는 수많은 시간과 비용이 소모된다. 하지만 블록체인 환경에서는 다양한 당사자들이 참여하는 환경에서 ‘신뢰’가 없어도 계약 관계를 맺을 수 있게 되었다.

블록체인이 분산화 비즈니스의 핵심이 되는 이유는 바로 네트워크 효과의 증대와 거래 비용(transaction cost)의 감소라고 여겨진다. 사람들은 이런 블록체인 기술이 불러오는 “가치의 인터넷(Internet of Value)”의 가능성을 보기 시작했으며, 이는 각자가 가진 기존 비즈니스 모델을 효율적인 분산화 구조로 바꾸는 것으로 이어질 것이다. 특히 블록체인 시스템에 내장되어있는 토큰 메커니즘은 네트워크 참여자들의 권리를 보장하는 방식을 제공하며 기존 비즈니스를 혁신할 것이다.
[\[1\]][1].

하지만, 블록체인 기술은 신생 기술이다. 다른 신생 기술들의 특성과 마찬가지로 아직은 다수의 단점들이 존재한다.

블록체인 기술은 제한된 성능, 거버넌스 메커니즘의 부재 등의 단점이 존재한다. 이런 단점들이 존재하기 때문에 현실적인 환경에서의 분산화 비즈니스 협업을 지원하기에는 부족함이 많다.

컨소시엄 체인(Hyperledger Fabric, R3 Corda, Ethereum Enterprise Alliance 등)은 이런 성능 및 거버넌스 문제를 해결하여 기업환경에 적합 블록체인을 만들기 위해 노력해왔다. 하지만 이런 컨소시엄 체인들은 거대한 기업들에 의해서만 주도되고 있다는 문제가 있다. 또한, 컨소시엄 체인들의 폐쇄적인 온체인(on-chain) 거버넌스 모델은 비효율적이다. 개방성과 토큰 이코노미 모델을 통해 대중들의 기대감을 받고 있는 퍼블릭 체인과는 달리, 컨소시엄 체인은 기술적 활력이 부족하다고 평가된다.

아이리스는 현존하는 블록체인 기술을 개선하여 수천개에서 수백만개의 중소 비즈니스(SMB, Small Medium Businesses)와 프리랜스 서비스 제공자들이 공존하며 보상을 받는 네트워크를 구상한다.

이를 현실화하기 위해서 다음과 같은 과제들이 해결되어아 할 것으로 보인다.


**모든 연산(computation)이 스마트 컨트랙트 같은 온체인(on-chain) 연산으로 구현될 필요는 없다**

이더리움[\[2\]][2]의 [튜링 완전(Turing-complete)](https://en.wikipedia.org/wiki/Turing_completeness) 가상머신은 ‘스마트 컨트랙트'를 구동한다. 사람들은 이런 스마트 컨트랙트를 이용해 탈중앙 애플리케이션을 만들 수 있을 것을 기대한다.

하지만 스마트 컨트랙트는 오직 결정론적 로직(deterministic logic)만을 처리할 수 있다 (모든 노드가 서로 동일한 상태(state)에 도달해야만 거래를 처리하고 블록을 생성할 수 있기 때문이다). 

하지만 다수의 비즈니스 로직들은 결정론적이지 않다. 환경적 매개변수(environmental parameter)와 시간 등 상황과 환경에 따라서 변화할 수 있다.

최근 들어 비즈니스 시스템들의 자연어 처리(NLP, Natural Language Processing), 머신 러닝, 그리고 오퍼레이션 연구 같은 컴퓨터 알고리즘에 대한 의존도가 증가하고 있다. 이런 알고리즘에는 더 나은 차선책을 찾으려고 노력하는 과정에서 로컬 최적 상태(local optimal state)에 묶여있지 않도록 빈번하게 의도적으로 임의성(randomness)을 추가한다.

다른 한 편으로, 일부 비즈니스 로직들은 오프체인(off-chain)에서 구동되는 것이 더 적합할 수 있고, 스마트 컨트랙트 같은 분산 복제 환경으로 구동되면 안되는 경우도 있다.

앞으로 블록체인 기술이 현실적으로 상용화 되기 위해서는 이런 오프체인 서비스를 분산원장에 이어주는 것이 핵심이다. 

**퍼블릭 체인, 컨소시엄 체인에 이미 존재하는 블록체인 리소스, 어떻게 재사용 할 것인가?**

하나의 퍼블릭 체인이 모든 유즈 케이스(use case)를 충족시키는 것은 불가능하다. 매일 새로운 블록체인 플랫폼이 세상에 소개되고, 각 프로젝트는 각자 분야에 특화된 솔루션을 제공한다.

암호화폐 데이터 사이트 코인마켓캡(Coinmarketcap)을 참고하면, 현재 무려 1천개 이상의 암호화폐들이 다양한 거래소에서 거래되고 있는 상황이다.

비즈니스 애플리케이션을 구축하기 위해서는 스토리지 솔루션, 데이터 피드 등이 필요하다. 그리고 시장에는 스토리지 (IPFS, SIA, Storj.io 등), 데이터 피드 (Augur, Gnosis, Oraclize 등) 그리고 사물인터넷(IOTA 등)과 같은 블록체인 서비스들이 존재한다. 아이리스는 이미 퍼블릭 블록체인으로 존재하는 해결책을 다시 고민하려고 하지 않는다. 오히려 이미 존재하는 퍼블릭 솔루션들을 기반으로 분산화 비즈니스 애플리케이션을 만드는 것이 더 효율적이라고 판단한다.

반면, 비즈니스 거래는 성능, 보안, 사업 운영 등의 이유로 컨소시엄/허가형 블록체인에 대한 필요성도 존재한다.
아이리스 네트워크가 보는 분산화 비즈니스 인프라 비전은 각자의 특성을 가진 수많은 블록체인들이 상호호환성을 가지며 공존하는 것이다. 그리고 이 비전의 가장 기본적이 필수 요소는 인터체인(Inter-chain) 기술이다.

~~하지만 지금까지의 인터체인 기술은 오직 토큰 수량의 이동(token value transfer)에 초점을 두었다. “다수의 체인이 제공하는 리소스는 어떻게 처리할 것일까?”에 대한 정답은 아직 나오지 않았다.~~

아이리스는 코스모스[\[3\]][3]와 폴카닷(Polkadot)[\[4\]][4] 같은 여러 인터체인 기술을 비교했다. 코스모스가 상호운용성(interoperability)과 확장성(scalability) 측면에서 더욱 성숙한 기반을 제공한다는 결론에 도달했다.

코스모스는 “다수의 허브, 다수의 존(many hubs and many zones)” 그리고 “각자의 거버넌스 모델을 가진 독립된 블록체인(each zones are independent blockchains having independent governance models)”의 블록체인 생태계를 지향한다. 코스모스가 설계한 블록체인 생태계의 디자인은 아이리스가 지향하는 실사용 가능한 서비스-지향 아키텍쳐(SOC, Service-Oriented Architecture)에 적합하다.

이런 이유로 아이리스는 코스모스 프레임워크를 기반으로 설계하였다. 아이리스 네트워크는 기존의 허브와 존으로 이루어진 탈중앙화 인터체인 네트워크에 코스모스/텐더민트[\[5\]][5] 기반의 서비스 인프라를 적용하였고, 토큰 활용성을 추가했다.

이 문서는 먼저 코스모스/텐더민트를 설명한 후, 아이리스 네트워크가 개발한 혁신들에 대한 설명으로 이어진다.

### 코스모스와 텐더민트 ################################################################

코스모스는 [\[3\]][3] ‘블록체인의 인터넷(Internet of Blockchains)’을 만드는 프로젝트다.

코스모스 생태계는 수많은 독립적인 “존(zone)”으로 이루어지며, 각 존은 [텐더민트](https://tendermint.com/) 같은 클래시컬 비잔틴 장애 허용(BFT, Byzantine Fault-Tolerant)~~여기에서는 코스모스 백서 따름~~ 합의 프로토콜을 중심으로 작동된다.

텐더민트는 엄격한 '포크 책임(fork accountability)'을 기반으로 악의적인 행위를 억제하여 일관성, 안전성, 고성능이 보장되는 BFT 합의 엔진을 제공한다. 텐더민트는 이더리움의 고성능 지분증명 구현 모델인 이더민트(Ethermint)[\[6\]][6] 같은 퍼블릭 블록체인 부터 오라클(Oracle) [\[7\]][7], CITA[\[8\]][8], 그리고 하이퍼렛저 버로우(Hyperledger Burrow)[\[9\]][9] 같은 안전성과 성능이 보장되어야 하는 컨소시엄/허가형 블록체인 까지 다양한 형태의 블록체인에 성공적으로 적용되었다.

현재 텐더민트는 코스모스 생태계의 첫 존이자 허브(Hub)인 '코스모스 허브'의 합의 프로토콜로 이용되고 있다. 허브는 다수의 존들과 연결될 수 있으며, 일종의 블록체인을 위한 가상 UDP/TCP 인 ~~'인터블록체인 통신???'~~(IBC, Inter-Blockchain Communication)을 통해 상호 통신이 가능하다. IBC를 통해 이동하는 토큰은 거래소 또는 제3자의 중개자 없이 코스모스 허브를 통해 한 존에서 부터 다른 존으로 안전하게 이동할 수 있다.

또한 코스모스 SDK를 이용해 누구나 상호호환이 가능한 블록체인을 개발할 수 있다. 일종의 '블록체인 스타터 키트'인 코스모스 SDK는 높은 적응성을 제공하여 목적에 따른 특수화 또한 가능하다.

### IRIS의 혁신 ################################################################

아이리스 네트워크는 분산화 비즈니스 애플리케이션 개발을 위한 기술적 기반을 제공하는 것이 목표다. 이런 점에서 아이리스는 디지털 자산에 특화되어있는 기존 블록체인  시스템과 차별점을 제공한다.

아이리스 네트워크를 통해 해결하려는 문제점의 두가지 핵심은 다음과 같다:
* 오프체인 컴퓨팅/오프체인 리소스와 분산원장의 연동성
* 다양한 형태의(heterogeneous) 블록체인 간의 상호운영성

우리는 코스모스/텐더민트 환경에 서비스 기반 인프라를 적용하여 해결하고자 한다.

아이리스의 설계는 수년간의 서비스 특화 아키텍처(SOA, Service-oriented Architecture)의 사고방식에서 유래한다. SOA는 명확한 경계, 공유 스키마(Shared Schema) 그리고 컨트랙트가 있는 자율서비스 설계 방식이다. [\[13\]][13] 초기 SOA는 엔터프라이즈 서비스 버스(ESB, Enterprise Service Bus) 같은 일종의공통 통신 버스(common communication bus)를 통해 서비스 간 통신을 가능하게 했다. 이런 '공통 통신 버스'는 서비스 제공자와 서비스 소비자가 공유하는 다수의 통신 지점을 연결해 상호 통신이 가능했다. 하지만 ESB 같은 중앙화된 운영 체계에는 단일 장애 지점(single point of fauilure)가 존재했으며, 서비스 배포에 대한 의존도가 있었다.

반면, 최근 들어 인기를 끌고 있는 마이크로-서비스 유형의 아키텍처는 SOA의 라이트 메시지 대기열(light message queues) 보다 ESB에 중점을 두며 한 단계 진보한 모습을 보이고 있다.

아이리스 네트워크의 서비스간 소통(Inter service communication)은 블록체인을 하나의 '신뢰 가능한 머신'으로 두며 비즈니스 협업을 중재하게 된다. 이런 형태의 시스템은 서비스 제공자와 서비스 소비자의 근본적인 '신뢰'가 없어도 소통이 가능하게 한다.

아이리스 네트워크는 텐더민트를 고성능 합의 엔진으로 적용했다. 텐더민트의 애플리케이션 특화 블록체인 인터페이스(ABCI, Application BlockChain Interface) 계층이 제공하는 유연성을 응용하여 서비스 권할 설정, 서비스 소비, 그리고 서비스 거버넌스를 일종의 '거래(transaction)'로 정의한다.

상단에서 설명했던 바와 같이, 대다수의 비즈니스 로직은 결정론적인(deterministic) 블록체인 스마트 컨트랙트로 구연하기에 부적절하다. 아이리스는 서비스 계층(service layer)을 이용해 비즈니스 애플리케이션에 특화된 로직을 블록체인 외로(off-chain) 통신하고 처리할 수 있게된다. 여기에서 블록체인은 이런 오프체인 서비스가 제공하는 결과(result)에 대한 합의를 제공하는 것에만 적용이 된다.

이런 아이디어는 라이트닝 네트워크의 오프체인 스테이트 채널(state channel)과 플라즈마의 사기방지 사이드체인(fraud proof side chains)에서 영감을 받았다. 아이리스는 사이드체인을 이용하지는 않지만, 기존 비즈니스 연산 로직을 블록체인 외에서 처리하고 추후 블록체인을 하나의 '합의 도구'로 이용한다는 것에서는 유사한 점이 있다.

코스모스 IBC는 인터체인 통신을 '한 체인의 계좌의 '값(value)'을 다른 체인의 계좌로 이동하는 것'으로 정의한다. 추가적으로, 아이리스 네트워크는 IBC를 통해 블록체인 간 연산(computation) 요청을 표준화하여 설계했다. 아이리스는 이런 기능이 확장 가능한 비즈니스 애플리케이션을 개발하기 위해서 필수라고 판단하며, 기능의 적용 가능 사례는 하단에 설명 되어있다.

아이리스 네트워크는 온체인 거래의 처리와 오프체인 데이터 프로세싱/비즈니스 로직 실행의 협엽이 가능한 서비스 인프라를 제공하기 위해 개발된다. 또한 IBC 기능을 향상하여 오프체인 데이터 프로세싱이 필요에 따라 크로스-체인 형태로 요청될 수 있게 한다.

아이리스 네트워크가 현재 가지고 있는 비전에는 스마트 월렛 같은 클라이언트 특화 도구를 제공하는 것 또한 포함되어있다. 해당 스마트 월렛은 크로스체인 멀티애셋 보관 및 관리 외에도 아이리스의 iService 이용도 가능할 것이다. 예를 들어, 특정 서비스 정의를 요청하는 소비자는 클라이언트 SDK를 이용해 서비스 제공자의 스켈레톤(skeleton) 또는 대다수의 프로그래밍 언어 기반의 소비자용 스텁(stub)을 생성할 수 있을 것이다.

<div STYLE="page-break-after: always;"></div>

## 아이리스 네트워크 디자인 ################################################################

![Figure of IRIS Network](https://github.com/irisnet/irisnet/blob/master/images/chap2-1.png?raw=true)

위 그림과 같이, 아이리스 네트워크는 코스모스 네트워크와 동일한 토폴로지(topology)를 기반으로 만들어진다. 아이리스는 아이리스 허브를 코스모스 허브와 연결하여 일종의 코스모스 존이자 지역 허브로 자리잡게 된다.

아이리스 SDK(코스모스 SDK를 기반으로 만들어져 아이리스에 특화된 확장된 기능을 제공하는 도구)를 기반으로 만들어진 아이리스 풀 노드(full node)들은 아이리스 네트워크의 서비스 인프라를 제공하며 IPFS(InterPlanetary File System) 노드의 기능을 내장 한다.

iService(아이리스 서비스, IRIS Services)는 블록체인 생태계와 기존 

IRIS Services (a.k.a. "iServices") intend to bridge the gap between the blockchain
world and the conventional business application world, by mediating a
complete lifecycle of off-chain services -- from their definition,
binding (provider registration), invocation, to their governance
(profiling and dispute resolution). By enhancing the IBC processing
logic to support service semantics, the IRIS SDK is intended to allow
distributed business services to be available across the internet of blockchains.

While the IRIS network focuses on providing an innovative solution
for distributed business applications, it is still part of
the broader Cosmos network.  All zones connected to our proposed IRIS hub would be able to interact with any other zone in the Cosmos network over
the standard IBC protocol.  Furthermore, by introducing a layer of service
semantics, which we believe could enable a whole new set of business scenarios,
the planned IRIS network would represent an increase in scale and diversity
of the Cosmos network.

### Network Actors

1. **Consumers** are those users who may consume off-chain services by sending
  requests to the network and receiving responses from the network.

2. **Providers** are those users who may offer the implementation of one or more
iService definitions and often act as *adaptors* of off-chain services and resources located
  in other public and consortium chains, as well as in enterprise legacy
  systems.  Providers monitor and process incoming requests and send responses
  back to the network.  A provider could at the same time act as a consumer
  by sending requests to other providers.  As planned, providers would be required to
  charge a fee for any services they might offer, and the service fee, by default, would be
  priced in the IRIS network's native fee token known as "IRIS"; providers
  could also price their services in other whitelisted Cosmos fee tokens, to be
  considered in due course.

3. **Profiler** is the special user who works on behalf of the IRIS Foundation
Limited ("Foundation"), a Hong Kong incorporated company limited by guarantee.
The Foundation will take the lead in building the IRIS network.  The profiler
is the sole user authorized to invoke iServices in the profiling mode, which
is intended to help create and maintain objective *provider profiles* that
consumers use to select suitable providers.

### IRIS Services

In this section, we set out the intended technical parameters for deploying iServices on the IRIS network.

**Service Definition**

A `Method` is composed of:

* `ID (int)`: The unique ID of this method in the encompassing iService

* `Name (string)`: The unique name of this method in the iService

* `Description (string)`: A description of this method

* `Input (string)`: A structured definition of the input parameters

* `Output (string)`: A structured definition of the output result

* `Error (string)`: A structured definition of all possible error conditions

* `OutputPrivacy (enum)`: Can be one of `NoPrivacy` or `PubKeyEncryption`

A `ServiceDefinition` is composed of:

* `Name (string)`: The name of this iService

* `Description (string)`: A description of this iService

* `Tags (string)`: Comma separated keywords about this iService

* `Creator (string)`: A self-description of the iService creator. *Optional*

* `ChainID (string)`: The ID of the blockchain where this iService was
  originally defined

* `Messaging (enum)`: Can be one of `Unicast` or `Multicast`

* `Methods ([]Method)`: The definition of methods available in this iService

A `CreateServiceDefinitionTx` transaction is composed of:

* `Definition (ServiceDefinition)`: The service definition to be created

**Service Binding**:

A `CreateServiceBindingTx` transaction is composed of:

* `DefinitionHash ([]byte)`: The hash of the service definition that the provider is binding to

* `ChainID (string)`: The ID of the blockchain where the provider is connected

* `ProviderAddress ([]byte)`: The provider's blockchain address

* `BindingType (enum)`: Can be one of `Local` or `Global`; choose `Global` if a
  provider wants the binding to be exposed to the rest of the world;
  otherwise, use `Local`

* `ProviderDeposit (int64)`: To create an effective binding, the provider
  must put down a deposit (in terms of IRIS token amount) that is greater than
  the value of the system parameter `MinProviderDeposit`; a larger deposit
  may imply more trustworthiness of the provider

* `ServicePricing (string)`: A structured definition of the service pricing
  model on a per method basis, including cost per call, volume discount,
  promotional terms etc.; service fee is by default listed in IRIS token but
  could also be quoted in other whitelisted fee tokens.

* `ServiceLevel (string)`: A structured definition of service level the
  provider agrees to bind himself to, in terms of response time,
  availability etc.

* `BindingExpiration (int64)`: The blockchain height where this binding
  expires; a negative number means "never expire"

An `UpdateServiceBindingTx` transaction is composed of:

* `DefinitionHash ([]byte)`: The hash of the service definition the
  provider has bound to

* `ChainID (string)`: The ID of the blockchain where the provider is
  connected

* `ProviderAddress ([]byte)`: The provider's blockchain address

* `ChangeSet (string)`: A structured definition of desired changes to an
  existing binding identified by the preceding three fields

![Figure of iService Definition and Bindings](https://github.com/irisnet/irisnet/blob/master/images/chap2-2.png?raw=true)

A provider can update `ServicePricing`, `ServiceLevel` and `BindingExpiration`
at any time, but a small amount of their deposit will be slashed for
changing the latter two (specified by `ServiceLevelUpdateSlash` and
`BindingExpirationUpdateSlash` respectively). Setting `BindingExpiration` to
a height that is lower than the current height will be interpreted as
invalidating the binding immediately.

Updates to `ProviderDeposit` will always be treated as *adding to* the
current deposit balance. Whenever the balance drops below
`MinProviderDeposit`, the binding will be disabled until the provider
increases the balance above the threshold. Upon expiration or
invalidation of a binding, the provider will automatically get back the
remaining balance of its deposit.

`BindingType` can be changed from `Local` to `Global`, but not the other way
around. To downgrade a binding from `Global` to `Local`, a provider must
first invalidate the binding in question and then create a new `Local`
binding.

If a provider somehow needs to move the binding to a new address, it is
not allowed to update `ProviderAddress` directly; instead, the provider
should invalidate the current binding and create another one with the
desired new `ProviderAddress`.

Upon successful execution of these two transactions by the application
(i.e., iService business logic in the IRIS SDK), a `ServiceBinding` object
will be created or updated accordingly.

A `ServiceBinding` is composed of:

* `DefinitionHash ([]byte)`

* `ChainID (string)`

* `ProviderAddress ([]byte)`

* `ServiceLevel (string)`

* `ServicePricing (string)`

* `BindingExpiration (int64)`

* `IsValid (enum)`: Can be one of `True` or `False`

**Service Invocation**

![Figure of Service Invocation](https://github.com/irisnet/irisnet/blob/master/images/chap2-3.png?raw=true)

Consumers and providers are proposed to interact with each other through *endpoints*.
There are two kinds of endpoints -- *request table* and *response table*
(see Figure above). Service requests are posted to request tables monitored
by interested provider(s) which pick up and process requests addressed
to them; service results (or errors) are posted back to response tables
monitored in turn by matched consumers.

For a `Multicast` service, all of its bindings share one request table;
for a `Unicast` service, however, a separate request table is created and
maintained for each of its bindings. As for the other direction, a dedicated response table would be created and managed for each consumer.

A `ServiceRequest` is composed of:

* `ChainID (string)`: The ID of the blockchain where the consumer is
  connected

* `ConsumerAddress ([]byte)`: The blockchain address of the consumer

* `DefinitionHash ([]byte)`: The hash of the service definition

* `MethodID (int)`: The ID of the method to be invoked

* `InputValue (string)`: A structured representation of input values

* `BindingHash ([]byte)`: The hash of the target binding, in case of a
  `Unicast` service. *Optional*

* `MaxServiceFee (int64)`: The max amount of service fee the consumer is
  willing to pay for a `Multicast` request. *Optional*

* `Timeout (int)`: The max number of blocks the consumer is willing to wait
  for response(s) to come back

A `PostServiceRequestTx` transaction is composed of:

* `Requests ([]ServiceRequest)`: The service requests to be posted

* `RequestDeposits ([]int64)`: The consumer must put down for each request
  a deposit (in terms of IRIS amount) that is greater than the value of
  `MinRequestDeposit`; this deposit is meant to incentivize the consumer to acknowledge receipt of service responses in a timely manner (see `ConfirmServiceResponseTx`).

The application will verify that each request is coming from a consumer
with matching `ChainID` and `ConsumerAddress`, the targeted binding is
valid, the request deposit is sufficient, the consumer's account balance is
enough to cover the request deposits and service fees, and that the total
number of requests in the transaction is less than `MaxRequestPostBatch`.

When a verified request is appended to the request table, the related
service fee (`MaxServiceFee` in case of a `Multicast` request) will be
deducted from the consumer's account and locked up in escrow.

A `GetServiceRequest` query is composed of:

* `DefinitionHash ([]byte)`: The hash of the service definition

* `BindingHash ([]byte)`: The hash of this provider's binding to the
  service in question; the application will verify that the binding is
  valid and the caller matches the binding's `ChainID` and `ProviderAddress`

* `BeginHeight (uint64)`: The blockchain height from where the application
  should start to retrieve requests for the provider, up to a total number
  that is the lesser of `BatchSize` and `MaxRequestGetBatch`

* `BatchSize (int)`: The max number of requests to be returned

A `ServiceResponse` is composed of:

* `RequestHash ([]byte)`: The hash of the matched request

* `BindingHash ([]byte)`: The hash of this provider's service binding

* `OutputValue ([]byte)`: A structured (potentially encrypted)
  representation of output result. *Optional*

* `ErrorMsg (string)`: A structured representation of error messages.
  *Optional*

A `PostServiceResponseTx` transaction is composed of:

* `Responses ([]ServiceResponse)`: The service responses to be posted

The application will verify that each response is coming from a
provider with matching `ChainID` and `ProviderAddress`, and that the number
of responses in the transaction is less than `MaxResponsePostBatch`. A
verified request will be appended to the response table for the intended
consumer.

A `GetServiceResponse` query is composed of:

* `RequestHash ([]byte)`: The hash of the original request; the
  application will verify that the caller matches the request's `ChainID`
  and `ConsumerAddress`

* `BeginHeight (uint64)`: The blockchain height from where the application
  should start to retrieve responses for the consumer, up to a total
  number that is the lesser of `BatchSize` and `MaxResponseGetBatch`

* `BatchSize (int)`: The max number of responses to be returned

A `ConfirmServiceResponseTx` transaction is composed of:

* `ResponseHash ([][]byte)`: The hash of responses to be confirmed

The application will verify that the each response to be confirmed is
indeed for a request originated by the caller, and that the number of
responses in the transaction is less than `MaxResponseConfirmBatch`.

Responses that fall out of the `Timeout` window (and, in case of `Multicast`
responses, when `MaxServiceFee` runs out as more responses come back) will
not be accepted by the application. A consumer starts processing a
`Unicast` response immediately upon receiving it. However, for `Multicast`
responses, a consumer will need to wait until the `Timeout` window elapses before
starting to process all responses received, if any.

When a `Unicast` response is confirmed by the consumer, the associated
service fee will be released from escrow to the matched provider account
-- after a small tax (defined by `ServiceFeeTaxRate`) is deducted and
added to the *system reserve*; and the associated request deposit will
be returned to the consumer as well.

In the case of a `Multicast` request, the situation is a bit more complex:
when a response is confirmed, only part of the request deposit is
returned to the consumer, in proportion to the response related service
fee vs `MaxServiceFee`; and after all responses are confirmed, the
remaining escrow balance for the request will be returned to the
consumer.

If a request timeouts without seeing any response come back, the
application will refund the associated balance held in escrow plus the request
deposit, in full, back to the consumer. However, if the consumer does
not confirm a response in time (before `ResponseConfirmTimeout` +
blockchain height of the response), a small penalty (defined by
`ResponseConfirmDelayPenaltyRate`) will be applied before the request
deposit is refunded to the consumer, while the associated service fee
will be released to the provider as usual.

**Dispute Resolution**

In any case where a consumer is unsatisfied with a service response, a mechanism should exist allowing the consumer to issue a complaint and consequently, to receive an acceptable solution to that complaint, without having to resort to a centralized authority such as the legal system.  Also, this mechanism should avoid
introducing subjective evaluation, which could be abused by either side.

The process to resolve a dispute that arises on the IRIS network resembles that of service invocation, except that a consumer sends a `Complaint` to the provider, and the provider responds with a `Resolution`.  These interactions are intended to happen through a pair of global endpoints known as *complaint table* and *resolution table*.

Under the present design for the IRIS network, a consumer deposit is required for filing a complaint.  Where a consumer does not confirm a resolution in a timely manner, a penalty will be deducted from this deposit.  Similarly, a provider's deposit will be partially slashed if he fails to respond to a complaint in a timely manner.

A `Complaint` is composed of:

* `ResponseHash ([]byte)`: The hash of the response in dispute

* `Problem (string)`: A description of the problem with the service response

* `PreferredDisposal (enum)`: Can be one of `Refund` or `Redo`

A Resolution is composed of:

* `ComplaintHash ([]byte)`: The hash of the matched complaint

* `Disposal (enum)`: Can be one of `Refund` or `Redo`

* `Refund (uint64)`: Service fee refund. *Optional*

* `OutputValue ([]byte)`: A structured (potentially encrypted)
  representation of output result. *Optional*

Our intended dispute resolution process, as outlined above, may not be legally binding.  Nonetheless, we believe that it will provide an efficient means of resolving common disputes on the IRIS network.

**Service Profiling**

Bootstrapping the iService ecosystem presents a few challenges.  A major challenge is finding a way to make it easy for consumers to discover suitable providers - consumers need performance metrics to evaluate and select a provider, yet without consumer usage no performance metrics will be available.

With the intention to solve this circular issue, we plan to introduce a profiling mechanism where a privileged system user, the profiler, invokes all the active services on a regular schedule.  This would leave objective performance data in the network (such as response time, availability, complaint handling etc.) that are useful for real consumers.

Service profiling calls would be exempt from service fees and consumer
deposits, but they would incur network transaction fees. These calls
would originate from a few reserved addresses that are intended to be recognized and honored by the application.

Profiling activities would stay at a relatively stable level for new services
and gradually decline for individual services as they start to
attract real consumer calls, which is expected to generate more performance data on their own.

Transaction fees incurred during profiling would be paid out from the system reserve by default, and the Foundation reserve would step in if necessary.

**Query**

All the service related lifecycle objects described above can be queried
using the ABCI Query interface [\[3\]][3]. These queries would be executed over
the Query connection and do not participate in the consensus process. We
have already seen how `GetServiceRequest` and `GetServiceResponse` queries
work as part of the service invocation process.

Below is a non-exhaustive summary of our currently planned queries:

**Service Objects**

| Object                               | Commonly Used Filters                | Authorization                        |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| Service Definition                       | Name, keywords, source (chain ID), messaging type, with active bindings... | Anyone can query                         |
| Service Binding (for a given definition) | Location (local or remote), pricing, service level, expiration... | Anyone can query                         |
| Service Request                          | Service definition and binding, blockchain height, batch size | Only matched provider(s) |
| Service Response                         | Service request, blockchain height, batch size | Only matched consumer                    |


**Performance Metrics**

| Area                    | Metrics                              | Authorization |
| --------------------------- | ---------------------------------------- | ----------------- |
| Provider (address)          | Number of services provided (ever and active), response time (min, max and average), requests served (local and remote), requests missed, complaints received, complaints ignored, ... | Anyone can query  |
| Provider (binding)          | Active time, response time (min, max and average), requests served (local and remote), requests missed, complaints received, complaints ignored, ... | Anyone can query  |
| Consumer          | Number of services ever used, requests made, requests confirmed (in time and missed), complaints made, resolutions confirmed, ... | Anyone can query  |
| Consumer (service, binding) | Requests made, requests confirmed (in time and missed), complaints made, resolutions confirmed, ... | Anyone can query  |


### IBC Enhancement

One unique advantage of establishing our service infrastructure on top of Cosmos is the potential for services to be *deployed once and invoked
everywhere*, over an internet of blockchains. Specifically, our plan is to
accomplish the following:

1. Service definitions are broadcast to every zone in the IRIS network;

2. Global service bindings are broadcast to every zone in the IRIS network;

3. Service requests or complaints targeting a remote provider are routed to
  the blockchain to which the provider is connected;

4. Service responses or resolution meant for a remote consumer are routed
  back to the blockchain to which the consumer is connected.

When processing a `CreateServiceDefinitionTx` transaction, the application
is designed to first validate and store the `ServiceDefinition` object locally, before creating an `IBCPacket` containing the definition for each neighboring chain.

Each neighbor eventually receives -- from the corresponding relay process --
an `IBCPacketTx` containing the packet; if the definition does not already
exist in the receiving chain, the latter will pass on the definition by
creating an `IBCPacket` for each of *its* neighbors -- except the source
chain from which it received the packet in the first place; if the
definition already exists, the receiving chain stops passing on the
definition.

Similarly, when a `ServiceBinding` is created or updated with its
`BindingType` set or updated to `Global`, an `IBCPacket` containing the
binding is created for each neighboring chain, and gets propagated across
the entire IRIS network.

An `IBCPacket` described above is composed of:

* `Header (IBCPacketHeader)`: The packet header

* `Payload (ServiceDefinition or ServiceBinding)`: The bytes of the service
  definition or binding

The `IBCPacketHeader` above is composed of:

* `SrcChainID (string)`: The ID of the blockchain creating this packet

* `DstChainID (string)`: The ID of the neighboring blockchain this packet is
  destined for

* `Number (int)`: A unique number for all packets

* `Status (enum)`: `NoAck`

* `Type (string)`: "iris-service-definition" or "iris-service-binding"

Now let's take a look at how interchain service invocation happens through IBC.
When a request is made for a `Unicast` service, the application checks if
the target binding is `Local`; where this is true, the `ServiceRequest` is appended to the corresponding request table as explained in 2.2; otherwise, an
`IBCPacket` containing the `ServiceRequest` will be created instead.

An `IBCPacket` containing a `ServiceRequest` is composed of:

* `Header (IBCPacketHeader)`: The packet header

* `Payload (ServiceRequest)`: The bytes of the service request

The `IBCPacketHeader` above is composed of:

* `SrcChainID (string)`: The ID of the blockchain creating this packet

* `DstChainID (string)`: The ID of the blockchain where the remote provider
  is located, i.e., `ServiceRequest.ServiceBinding.ChainID`

* `Number (int)`: A unique number for all packets

* `Status (enum)`: `AckPending`

* `Type (string)`: "iris-service-request"

* `MaxHeight (int)`: Current height + `ServiceRequest.Timeout`

As a remote request finally arrives at the destination chain, the
application would append it to the corresponding endpoint (the request table)
for the targeted binding. A response to this remote request would be
wrapped in a receipt `IBCPacket` that is routed all the way back to the
source chain and appended to the remote endpoint (the response table) for
the originating consumer.

Request for a remote `Multicast` service is treated in the same way except
that more than one `IBCPacket` could be generated in the source chain.

Remote complaints and resolutions are expected to work in the same manner as requests and responses, and therefore will not be elaborated here.

Below is a complete list of application-dependent `IBCPacket` types:

| **Type**                  | **iService Object** |
| ------------------------- | ------------------- |
| "iris-service-definition" | ServiceDefinition   |
| "iris-service-binding"    | ServiceBinding      |
| "iris-service-request"    | ServiceRequest      |
| "iris-service-response"   | ServiceResponse     |
| "iris-complaint"          | Complaint           |
| "iris-resolution"         | Resolution          |

<div STYLE="page-break-after: always;"></div>

## Use Cases ################################################################

In this section, we have set out some potential use cases for the IRIS network.

### Distributed AI for privacy preserving data analysis

The proposed service infrastructure has been prototyped by Bianjie AI, a
Shanghai based startup, into its permission product `BEAN (Blockchain
Edge Analytics Network)` to solve the longstanding challenge of getting
data for running analytics models. Although homomorphic encryption is
one of the key methods allowing computing to be achieved over encrypted data, it is said to be unable to practically solve real world machine learning problems due to its slow performance. As a result, BEAN was created to take a different approach. This approach uses the idea of model parallelism taken from the traditional distributed AI study [\[14\]][14] and
utilizing SOA design patterns to develop distributed analytics services as an additional layer to the blockchain.

To protect data access, the (partial) model that runs on the data side needs to be open sourced to the client and specified in the service definition. Since only the partial model is released to the client, the model developers do not have to worry about someone stealing their idea; equally, the data owners never need to worry about losing control of data usage as their data will not be leaving its origin.

Other potential benefits could include the following:
1.	Only a small amount of parametric data being exchanged on-chain, which can help enhance performance.

	.	A more practical way for data usage auditing, which is often needed in the healthcare domain.

Healthcare data is highly private, involving numerous security requirements. This puts forward the challenge for healthcare data to be used for the purposes of cross-organization collaboration (such as a cross-hospital clinic records search for diagnosis assistance, new drug clinic test patient identification, health insurance automatic claim processing etc.). This minimum viable product ("MVP") service layer implementation is built on top of `Ethermint` in attempt to connect hospitals, insurance companies and analytics service providers to provide privacy preserving healthcare data analytics capability.

Smart contracts have been implemented to support on-chain service registration and invocation. One example of the off-chain data processing could be to support a Diagnosis Related Group ("DRG") grouping analytics service. More specifically, when a hospital user invokes the DRG service, the raw medical record is processed off-chain using service provider provided client side NLP (implemented as SQL and Python) code stub to exact structured data inputs for receiving DRGs service over blockchain without passing the highly confidential raw medical records.

The `BEAN`
scenario demonstrates a more complicated service use case including
implementing distributed analytics, and connecting service providers as
well as service consumers, utilizing blockchain to provide audible
transaction ledge as well as trustworthy distributed computing
foundation.

### Data and analytics e-marketplace

From studying several proposed AI+Blockchain projects, it seems that most of the projects aim to provide data exchange markets and analytics API markets. With proposed `IRIS` infrastructure, those
networks could potentially be built with ease through publishing data as data services and wrapping analytics API as analytics services utilizing the `IRIS` service provider SDK.

### Distributed e-commerce

With the proposed `IRIS` infrastructure, integration with traditional systems
like `ERP` to obtain inventory information, or inter-chain query on trusted data sources to obtain information such as transportation and weather data, will be quite similar to the approach with which many enterprise application developers are already familiar. With those services integrated to support
distributed e-commerce applications, it could be possible for distributed e-commerce applications to provide a similar user experience as centralized systems, such as Amazon or Alibaba.

### Combining public chains & consortium chains

For many business scenarios, taking a hybrid architecture of combining the good features of a public chain and a consortium chain can provide beneficial results, particularly with regards to performance, security and economic incentives.

For example, hospitals and insurance companies could form a consortium blockchain to support high performance medical insurance transactions, whilst identifying other information such as statistics regarding certain diseases as a global service, which can be invoked from other public chains. The tokens received from public chains can be awarded back to
those information providers in the consortium chain, which motivate the
system participants to improve and promote services. With this infrastructure provided by `IRIS`, large-scale spontaneous collaboration could be made possible while still supporting stringent performance and security requirements.

There are many use cases that could be supported by the `IRIS` service
infrastructure, such as more efficient asset based security systems,
distributed regulation technology such as due diligence, mutual aid
marketplace etc. One of `IRIS` project plans is also working closely with
such application project teams to support and enable them with needed
blockchain infrastructure and allow them to focus on delivering the
envisioned business value more efficiently.

<div STYLE="page-break-after: always;"></div>

## Token Economics ################################################################

Similar to the Cosmos Network, the IRIS network, as presently designed, is intended to support a multi-token model. The tokens will be held on the various zones, and can be moved from one zone to another via the IRIS Hub. There are two types of tokens that are expected to support IRIS network's operation:

* staking token
* fee token

### Staking token

Adopting the same staking mechanism design used in the Cosmos network [\[15\]][15], the IRIS Hub will have its own special native token for staking. This token will be called "IRIS". We have a number of ideas in mind regarding the specific functionality of the IRIS token, including:

* integration of the IRIS token in the IRIS network's consensus engine validators, through a system of validators and delegators;

* voting power to participate in the IRIS network's governance


### Fee token

There are two types of fee tokens in IRIS network:
* **Network fee** token is for spam-prevention and payment to validators in maintaining the
  ledger;
* **Service fee** token is used for payment to service providers
  who deploy iServices and the default payment service token is IRIS token.

The IRIS network is intended to support all whitelisted fee tokens from the Cosmos network, e.g [Photon](https://blog.cosmos.network/cosmos-fee-token-introducing-the-photon-8a62b2f51aa), plus the IRIS token.

Supporting a variety of whitelisted fee tokens is a feature that we plan to adopt from Cosmos. It can provide an enhanced experience for network participants. In Cosmos, for `network fee token`, each validator has a config
file defines his personal weighting of how much they value each fee
token. Validator can run a separate cron job to update the config file
based on validator preferred live market data or maybe just use a
default config value.

For the `service fee token` design, similarly a multi-token model is planned to be supported.  A service provider on the IRIS network should therefore have the freedom to charge for their services in their preferred tokens, provided that it appears on the whitelist.

To help IRIS network participants mitigate cryptocurrency price volatility, the Foundation intends to facilitate the deployment of global iServices for retrieving market data from different exchanges, or through the potential introduction of oracles.

Both staking and fee tokens are subject to further refinement to ensure compliance with legal and regulatory obligations.

<div STYLE="page-break-after: always;"></div>

## Initial Token Distribution ################################################################

On Genesis, the initial token supply will be 2,000,000,000 IRIS tokens.  The distribution of IRIS tokens is planned to be as follows:

* **Private Sale**: 25%

* **Bianjie Developer Team**: 15% (4-year vesting period starting from IRIS Hub launch, during which the team will vest 1/48th of its IRIS tokens each month)


* **Tendermint Developer Team**: 10% (2-year vesting period starting from IRIS Hub launch, during which the team will vest 1/24th of its IRIS tokens each month)

* **IRIS Foundation**: 15% (reserved to support the operations of the Foundation)

* **Ecosystem Development**: 30% (swap with zones connecting to IRIS Hub; grant to potential users; awards to outstanding partners; potential public sale)

* **Cosmos ATOM Holder Airdrop**: 5% (airdrop to ATOM holders through a special airdrop to a wallet owned by the Cosmos Hub for ATOM holders subject to an one year vesting period. The vesting period will begin on the date of the IRIS Hub Launch, and the tokens will vest monthly over a one-year period such that 1/12th of the tokens vest each month).

If and when the IRIS network is fully deployed, the annual inflation rate of IRIS tokens will be adjusted to account for the fact that a substantial portion of IRIS tokens in circulation may be voluntarily staked by participants to participate in the consensus engine.

Proceeds from the private sale of IRIS tokens will be used, first and foremost, for the development of the IRIS network. The planned usage distribution is as follows:

* **Foundation Operations**: 10% (including service providers and contractors fees, for example, auditing, consulting, legal and other third party fees, and other overheads)

* **Software Development**: 50% (including costs, fees and expenses directly attributable to the development of launch)

* **Developer Enablement**: 10% (including funding hackathons, awards to volunteers and training programs)

* **Research and Development Sponsorships**: 10% (including conference, research programs and university outreach)

* **Marketing and Promotion**: 20% (including business development, community programs and outreach, together with related travel, communication, publication, distribution and other expenses)


<div STYLE="page-break-after: always;"></div>

## Roadmap ################################################################

The expected IRIS project is set out below. We reiterate that the roadmap is indicative only, and subject to change.

* **PANGU** (January 2018 \~ March 2019) The first stage of the IRIS project will focus on having the IRIS Hub up and running. We also intend to release an initial version of the mobile client for the IRIS network. In this stage we also  focus on building the fundamental IRIS Service Layer. This will involve enabling service definition, binding, invocation and query. We plan to collabrate with 1-2 ecosystem parteners to release i-Services to IRIShub.  

* **NUWA** (April 2019 \~ September 2019) In this stage we are aiming to have a beta version of the IRIS SDK ready for developers. We plan to upgrade IRISnet mobile client to support i-Services. We plan to establish collabrations with application specific blockchains and enable them as zones connecting to IRIShub. We also plan to accomplish the connection with Cosmos Hub at this stage.
 
 
* **KUAFU** (Oct 2019 \~ Dec 2019) The third stage will focus on incremental upgrades to the IRIS network in order to support our planned advanced IRIS Service governance features.


* **HOUYI** (Beyond January 2020)
The fourth stage will focus on further technology innovations to the IRIS network, IRIS SDK and mobile client, as well as developer engagement.

<div STYLE="page-break-after: always;"></div>

## The Team ################################################################

**Bianjie **
is the core development team for the IRIS network, leveraging the team's experience established from building distributed applications. [Bianjie](https://www.bianjie.ai) is a Shanghai-based start-up established in 2016. It focuses on developing innovative products and solutions for healthcare and financial industries, using advanced Blockchain and AI technologies. Besides IRISnet, Bianjie's also building another core product ---  `BEAN (Blockchain Edge Analytics Network)` BEAN (Blockchain Edge Analytics Network), which is a permission chain which delivers distributed data analytics services for privacy preserving healthcare data analysis and exchange using NLP and machine learning technologies.
**Bianjie AI**
is also the operation and service partner of Cosmos Network in China.

**Tendermint** (the team that developed the [Tendermint](https://www.tendermint.com) consensus engine and is currently building Cosmos), **Wancloud** (a subsidiary of [Wanxiang
Blockchain](http://www.wxblockchain.com) are strategic parteners working together with **Bianjie AI** building the IRIS network's infrastructure.  

Tendermint's intended role to give technical advice and development support to the IRIS project team in extending the Tendermint ABCI and the Cosmos IBC technologies.
[Wancloud](https://www.wancloud.io) is envisaged as the key strategy partner to both the Cosmos and IRIS ecosystems, and we understand that it intends to participate in Cosmos and IRIS development across Asia.

### Core Members

**Haifeng Xi**

[Haifeng](https://www.linkedin.com/in/haifengxi/) is a senior technologist and entrepreneur. Haifeng has an M.S degree in ECE from the University of Maryland. Haifeng worked as CTO for Wanxiang Blockchain Wancloud before starting IRISnet project. He also worked as senior architect for two leading financial companies In US (Tudor Investment & RBS Sempra), then he came back to China worked in the capacity of CTO for three companies, one of which is NASDAQ listed (China Finance Online).


**Harriet Cao**

[Harriet](https://www.linkedin.com/in/harrietcao/) is the founder of Bianjie AI, which a Shanghai-based start-up focusing on building smart services for blockchain that enable trustworthy and efficient business collaborations using distributed AI technology. Harriet is an award-winning practitioner of data analytics and artificial intelligence technologies, and was the recipient of 2010 INFORMS Daniel H. Wagner Prize. Prior to establishing Bianjie AI, Harriet worked for IBM Research for more than 16 years in various capacities including Director of IBM Research Shanghai Lab and Big Data Analytics Leader for IBM Global Labs.
Harriet has an M.S degree in Robotics from Carnegie Mellon University and an M.S. degree in Automation Control from Tsinghua University.

**Jae Kwon**

After graduating from Cornell in 2005 with an undergraduate degree in computer science, [Jae](https://www.linkedin.com/in/yjkwon/) worked as a software developer in Silicon Valley, first at Amazon (where he worked on the Alexa digital assistant), then later at Yelp, where he led their mobile app development team.
After getting the blockchain bug, Jae created the Tendermint BFT consensus algorithm and the Tendermint Core blockchain engine, with the intent of creating a provably secure proof-of-stake algorithm.
In addition to Tendermint, Jae is also the creator of Cosmos.


**Tom Tao**

Since joining Wanxiang in August 2016, [Tom](https://www.linkedin.com/in/tom-tao-14763a45/) is responsible for Wanxiang Blockhain Group's consulting service, Wancloud BaaS Platform as well as the ChainBase accelerator and incubator service. Before Wanxiang, Tom worked in service management and business management for over 18 years in a number of global leading companies.
Tom has spearheaded the introduction of cloud services, IoT data service platforms, and creative accelerator technologies into the Chinese market.
Tom has been tracking trends in the blockchain, cloud computing, IoT and smart manufacturing industries since 2013. Tom has a Master's degree in Physics from Fudan University and a Bachelor's degree in Electrical Engineering from Nankai University.


### Advisors

**Dr. Shuo Bai**

Dr. Bai is the director of ChinaLedger Technical Committee, and former Chief Architect of Shanghai Stock Exchange. He is a senior blockchain professional who graduated from Peking University with doctorate of science. He worked in various capacities including researcher, doctoral student advisor, director of software department, and chief scientist in the Institute of Computing Technology, Chinese Academy of Sciences. He also led the establishment of China National Internet Emergency Center (CNCERT/CC) since 2000. Dr. Bai has rich experiences in theoretical research and technical practices in the fields of financial exchanges, consortium and public blockchains.

**Jim Yang**

[Jim Yang](https://www.linkedin.com/in/jimyang/) runs Strategy for Tendermint. He was the founder and CEO at ChatX, mobile messaging studio. ChatX developed various mobile messaging/social apps. He also co-founded Identyx, where he served as CEO until its acquisition by Red Hat. Identyx developed an open source enterprise identity management software.

**Zaki Manian**

[Zaki Manian](https://zaki.manian.org), Executive Director of Trusted IoT Alliance, is a prolific contributor to the development of blockchain and cryptocurrency technology. Zaki has deep expertise in cryptography and distributed consensus system. He is also an advisor to the Cosmos project, and several other investment funds and startup in the space.

**Adrian Brink**

[Adrian Brink](https://adrianbrink.com), Core Developer & Head of Community of Tendermint / Cosmos Network.

**Michael Yuan**

[Dr. Michael Yuan](http://www.michaelyuan.com) is the Director of the [CyberMiles Foundation](https://cm.5miles.com). Michael received a PhD in Astrophysics from University of Texas at Austin. He is the author of 5 books on software development, published by Prentice Hall, Addison-Wesley, and O'Reilly. Michael was an active code committer in large Open Source projects such as Firefox, Fedora, JBoss, and others. He is an expert on enterprise and mobile software, and was a Principle Investigator on multiple research projects funded by the US government.

**Yubo Ruan**

[Yubo](https://www.linkedin.com/in/yubo-ruan/) is the founder of 8 Decimal Capital. The fund invested in IRISnet，0x、Kyber、Ontology、Fcoin、Zilliqa、ICON、Wanchian、Bibox、BiShiJie. Yubo is the co-founder of Skylight Investment, a boston based venture fund backed by New Oriental(NYSE:EDU). Previously, Yubo started two highly successful companies, including Alisimba (Acquired by TopHacker Group) held 4 national patents and won the 2017 AACYF 30 under 30, Silver Medal Winner, iENA International Inventions Competition, 2012.

<div STYLE="page-break-after: always;"></div>

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
[11]: https://www.plasma.io/plasma.pdf
[12]: https://github.com/cosmos/ibc/blob/master/README.md
[13]: https://www.amazon.com/SOA-Principles-Service-Thomas-Erl/dp/0132344823
[14]: http://www.cs.toronto.edu/~ranzato/publications/DistBeliefNIPS2012_withAppendix.pdf
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

* [13] Thomas Erl,  "SOA: Principles of Service Design", Prentice Hall;
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
