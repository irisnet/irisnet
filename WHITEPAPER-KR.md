# IRIS Network 백서
**신뢰가능한 분산화 비즈니스 애플리케이션을 위한 인터체인 서비스 인프라 프로토콜.**

Haifeng Xi haifeng@bianjie.ai<br/>
Harriet Cao harriet@bianjie.ai

_NOTE: 원문 백서는 [아이리스 GitHub]<https://github.com/irisnet/irisnet/blob/master/WHITEPAPER.md>에 있으며 내용이 활발하게 업데이트되고 있습니다. 정기적으로 업데이트를 확인하십시오!_
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

하지만 지금까지의 인터체인 기술은 오직 토큰 수량의 이동(token value transfer)에 초점을 두었다. “다수의 체인이 제공하는 리소스는 어떻게 처리할 것일까?”에 대한 정답은 아직 나오지 않았다.

아이리스는 코스모스[\[3\]][3]와 폴카닷(Polkadot)[\[4\]][4] 같은 여러 인터체인 기술을 비교했다. 코스모스가 상호운용성(interoperability)과 확장성(scalability) 측면에서 더욱 성숙한 기반을 제공한다는 결론에 도달했다.

코스모스는 “다수의 허브, 다수의 존(many hubs and many zones)” 그리고 “각자의 거버넌스 모델을 가진 독립된 블록체인(each zones are independent blockchains having independent governance models)”의 블록체인 생태계를 지향한다. 코스모스가 설계한 블록체인 생태계의 디자인은 아이리스가 지향하는 실사용 가능한 서비스-지향 아키텍쳐(SOC, Service-Oriented Architecture)에 적합하다.

이런 이유로 아이리스는 코스모스 프레임워크를 기반으로 설계하였다. 아이리스 네트워크는 기존의 허브와 존으로 이루어진 탈중앙화 인터체인 네트워크에 코스모스/텐더민트[\[5\]][5] 기반의 서비스 인프라를 적용하였고, 토큰 활용성을 추가했다.

이 문서는 먼저 코스모스/텐더민트를 설명한 후, 아이리스 네트워크가 개발한 혁신들에 대한 설명으로 이어진다.

### 코스모스와 텐더민트 ################################################################

코스모스는 [\[3\]][3] ‘블록체인의 인터넷(Internet of Blockchains)’을 만드는 프로젝트다.

코스모스 생태계는 수많은 독립적인 “존(zone)”으로 이루어지며, 각 존은 [텐더민트](https://tendermint.com/) 같은 클래시컬 비잔틴 장애 허용(BFT, Byzantine Fault-Tolerant) 합의 프로토콜을 중심으로 작동된다.

텐더민트는 엄격한 '포크 책임(fork accountability)'을 기반으로 악의적인 행위를 억제하여 일관성, 안전성, 고성능이 보장되는 BFT 합의 엔진을 제공한다. 텐더민트는 이더리움의 고성능 지분증명 구현 모델인 이더민트(Ethermint)[\[6\]][6] 같은 퍼블릭 블록체인 부터 오라클(Oracle) [\[7\]][7], CITA[\[8\]][8], 그리고 하이퍼렛저 버로우(Hyperledger Burrow)[\[9\]][9] 같은 안전성과 성능이 보장되어야 하는 컨소시엄/허가형 블록체인 까지 다양한 형태의 블록체인에 성공적으로 적용되었다.

현재 텐더민트는 코스모스 생태계의 첫 존이자 허브(Hub)인 '코스모스 허브'의 합의 프로토콜로 이용되고 있다. 허브는 다수의 존들과 연결될 수 있으며, 일종의 블록체인을 위한 가상 UDP/TCP 인 IBC(Inter-Blockchain Communication)을 통해 상호 통신이 가능하다. IBC를 통해 이동하는 토큰은 거래소 또는 제3자의 중개자 없이 코스모스 허브를 통해 한 존에서 부터 다른 존으로 안전하게 이동할 수 있다.

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

코스모스 IBC는 인터체인 통신을 '한 체인의 계좌의 '값(value)'을 다른 체인의 계좌로 이동하는 것'으로 정의한다. 추가적으로, 아이리스 네트워크는 IBC를 통해 블록체인 간 연산(computation) 요청 형식을 표준화하여 설계했다. 아이리스는 이런 기능이 확장 가능한 비즈니스 애플리케이션을 개발하기 위해서 필수라고 판단하며, 기능의 적용 가능 사례는 하단에 설명 되어있다.

아이리스 네트워크는 온체인 거래의 처리와 오프체인 데이터 프로세싱/비즈니스 로직 실행의 협엽이 가능한 서비스 인프라를 제공하기 위해 개발된다. 또한 IBC 기능을 향상하여 오프체인 데이터 프로세싱이 필요에 따라 크로스-체인 형태로 요청될 수 있게 한다.

아이리스 네트워크가 현재 가지고 있는 비전에는 스마트 월렛 같은 클라이언트 특화 도구를 제공하는 것 또한 포함되어있다. 해당 스마트 월렛은 크로스체인 멀티애셋 보관 및 관리 외에도 아이리스의 iService 이용도 가능할 것이다. 예를 들어, 특정 서비스 정의를 요청하는 소비자는 클라이언트 SDK를 이용해 서비스 제공자의 스켈레톤(skeleton) 또는 대다수의 프로그래밍 언어 기반의 소비자용 스텁(stub)을 생성할 수 있을 것이다.

<div STYLE="page-break-after: always;"></div>

## 아이리스 네트워크 디자인 ################################################################

![아이리스 ](https://github.com/irisnet/irisnet/blob/master/images/chap2-1.png?raw=true)

위 그림과 같이, 아이리스 네트워크는 코스모스 네트워크와 동일한 토폴로지(topology)를 기반으로 만들어진다. 아이리스는 아이리스 허브를 코스모스 허브와 연결하여 일종의 코스모스 존이자 지역 허브로 자리잡게 된다.

아이리스 SDK(코스모스 SDK를 기반으로 만들어져 아이리스에 특화된 확장된 기능을 제공하는 도구)를 기반으로 만들어진 아이리스 풀 노드(full node)들은 아이리스 네트워크의 서비스 인프라를 제공하며 IPFS(InterPlanetary File System) 노드의 기능을 내장 한다.

iService(아이리스 서비스, IRIS Services)는 블록체인 생태계와 기존 비즈니스 애플리케이션 생태계를 이어주는 다리 역할을 한다. iService는 오프체인 서비스의 서비스 정의 부터 서비스 바인딩(binding), 서비스 요청(invocation), 거버넌스(프로파일링과 분쟁 해결)까지 서비스 라이프사이클(lifecycle)의 포괄적인 중재 역할을 한다.  아이리스 SDK는 IBC 처리 로직에 서비스 의미(service semantics)를 지원하여 분산화 비즈니스 서비스가 블록체인에도 제공될 수 있게 한다.

아이리스 네트워크는 자체적으로 혁신적인 분산화 비즈니스 솔루션을 제공하는데 초점을 두지만, 포괄적인 코스모스 생태계의 일원이기도 하다. 그렇기 때문에, 아이리스 허브에 연결된 모든 존은 표준 IBC 프로토콜을 이용해 코스모스 네트워크에 있는 모든 존들과 소통할 수 있다. 또한, 아이리스는 서비스 의미(service semantics) 계층을 추가하여 새로운 비즈니스 시나리오들이 펼쳐지며 코스모스 생태계 크기와 다양성을 키우는데 기여할 것으로 기대하고 있다.

### 네트워크 참가자

1. **소비자** 네트워크에 요청을 하고 응답을 받아 오프체인 서비스를 사용하는 유저.

2. **서비스 제공자** 하나 또는 그 이상의 iService 정의의 제공자로써 오프체인 서비스와 다른 퍼블릭/컨소시엄 블록체인/기존 엔터프라이즈 시스템의 리소스를 제공하는 유저이다. 서비스 제공자는 들어오는 요청을 모니터링한 후 처리하고, 네트워크에 응답(response)한다. 서비스 제공자는 소비자와 동일하게 다른 프로바이더에게 서비스 요청을 할 수도 있다.

현재 계획으로써는 서비스 제공자는 본인이 제공하는 서비스에 대해서 일정의 수수료를 요청해야 한다. 이때 수수료는 아이리스 네트워크의 고유 토큰 IRIS로 지불된다. 서비스 제공자는 본인이 승인한 다른 코스모스 수수료 토큰으로 제공받을 수 있는 방안은 추후 검토할 예정이다.

3. **프로파일러** 홍콩의 기업인 아이리스 재단(IRIS Foundation Limited)을 대표하여 일하는 유저이다. 프로파일러는 아이리스 네트워크에서 유일하게 '프로파일링 모드(profiling mode)'로 iService 요청을 할 수 있는 유저이다. 프로파일러는 소비자들이 서비스 제공자를 선택할때 이용할 수 있는 서비스 제공자 프로파일을 제공하는 일을 한다.

### 아이리스 서비스

이하 아이리스 네트워크에 iService를 전개하는 기술적 파라미터를 정의한다.

**서비스 정의**

`Method` 는 다음과 같은 값으로 구성된다:

* `ID (int)`: 해당 iService 메소드(method)의 고유 아이디

* `Name (string)`: 해당 iService 메소드의 고유 이름

* `Description (string)`: 메소드 설명

* `Input (string)`: 인풋 파라미터들에 대한 구조화된 정의

* `Output (string)`: 아웃풋 값에 대한 구조화된 정의

* `Error (string)`: 모든 에러 변수에 대한 구조화된 정의

* `OutputPrivacy (enum)`: `NoPrivacy` 또는 `PubKeyEncryption` 중 하나

`ServiceDefinition` (서비스정의) 는 다음과 같은 값으로 구성된다:

* `Name (string)`: 해당 iService의 이름

* `Description (string)`: 해당 iService 설명

* `Tags (string)`: 해당 iService의 키워드. 쉼표(,)로 분기된다

* `Creator (string)`: iService 제작자 소개 문구 *선택 사항*

* `ChainID (string)`: iService가 처음 정의된 블록체인의 ID

* `Messaging (enum)`: `Unicast` 또는 `Multicast` 중 하나

* `Methods ([]Method)`: 해당 iService에서 이용 가능한 메소드들의 정의

`CreateServiceDefinitionTx` 트랜잭션은 다음과 같은 값으로 구성된다:

* `Definition (ServiceDefinition)`: 생성되는 서비스 정의

**서비스 바인딩**:

`CreateServiceBindingTx` 는 다음과 같은 값으로 구성된다:

* `DefinitionHash ([]byte)`: 서비스 제공자가 바인딩하는 서비스 정의의 해시값

* `ChainID (string)`: 서비스 제공자가 연결되어있는 블록체인의 ID

* `ProviderAddress ([]byte)`: 서비스 제공자의 블록체인 주소

* `BindingType (enum)`: `Local` 또는 `Global` 중 하나; 서비스 제공자가 본인의 바인딩이 전 세계의 공계되는 것을 원하는 경우 `Global`을 입력한다. 그렇지 않은 경우 `Local`을 선택한다

* `ProviderDeposit (int64)`: 유효한 바인딩을 만들기 위해서 서비스 제공자는 시스템의 `MinProviderDeposit`이 정의하는 값 보다 많은 수량의 아이리스 토큰을 보증금(deposit)으로 예치해야 한다. 예치금이 많을 수록 서비스 제공자의 신뢰도가 높은 것을 알릴 수 있다

* `ServicePricing (string)`: 각 메소드 별로 체계적으로 정리된 서비스의 가격 모델. 요청별 가격, 대량 요청 할인, 할인 행사 등이 있을 경우 모두 포함 되어야 한다. 서비스 가격 지불 수단은 기본적으로 IRIS 토큰으로 정의되나, 서비스 제공자가 원하는 수수료 토큰을 화이트리스트에 추가할 수 있다

* `ServiceLevel (string)`: 반응 시간(response time), 사용 가능여부(availability) 같은 서비스 제공자가 보장하는 서비스 레벨의 정의

* `BindingExpiration (int64)`: 해당 바인딩의 유효성이 만료되는 블록 높이. 마이너스 값은 '만료되지 않음'을 뜻함

`UpdateServiceBindingTx` 는 다음과 같은 값으로 구성된다:

* `DefinitionHash ([]byte)`: 서비스 제공자가 바인딩 한 서비스 정의의 해시값

* `ChainID (string)`: 서비스 제공자가 연결되어있는 블록체인의 ID

* `ProviderAddress ([]byte)`: 서비스 제공자의 블록체인 주소

* `ChangeSet (string)`: 특정 바인딩의 `DefinitionHash`, `ChainID`, `ProviderAddress` 값의 변경을 체계적으로 나열한 값

![iService 정의와 바인딩](https://github.com/irisnet/irisnet/blob/master/images/chap2-2.png?raw=true)

서비스 제공자는 `ServicePricing`,`ServiceLevel` 그리고 `BindingExpiration`의 값을 언제나 변경할 수 있다. 하지만 `ServiceLevel`과 `BindingExpiration`값을 바꿀 경우 소량의 예치금이 `BindingExpirationUpdateSlash` 와`ServiceLevelUpdateSlash`의 로직에 따라 슬래싱 될 수 있다. 만약 `BindingExpiration`의 블록높이 값이 현재 블록높이보다 낮게 설정된 경우, 해당 바인딩은 즉시 무효처리 된다.

`ProviderDeposit` 값의 변경은 언제나 현재 예치금에 예치금을 *추가*하는 것으로 간주한다. 만약 예치금이 `MinProviderDeposit`값 보다 낮아질 경우, 모든 바인딩 행위는 최소 예치금 값을 넘을 때까지 비활성화된다. 만약 특정 바인딩이 무효처리 되었거나 만료된 경우, 서비스 제공자는 본인의 예치금을 자동으로 돌려받게 된다.

`BindingType`는 `Local` 값에서 `Global`값으로 변경될 수 있지만, 반대로 `Global`에서 `Local`로 변경이 불가능하다. 반약 서비스 제공자가 본인의 바인딩을 `Global`에서 `Local`로 변경을 원하는 경우, 해당 바인딩을 우선 무효처리 한 후 새로운 `Local`바인딩을 생성해야 한다.

`ProviderAdress` 값은 변경될 수 없다. 만약 서비스 제공자가 특정 바인딩을 새로운 주소로 이동해야하는 경우, 기존 바인딩을 무효처리 한 후 변경된 `ProviderAddress`값이 입력된 새로운 바인딩을 생성해야 한다.

애플리케이션이 위 두개의 트랜잭션이 성공적으로 처리되면, `ServiceBinding` 오브젝트가 생성/변경된다.

`ServiceBinding` 은 다음과 같은 값으로 구성된다:

* `DefinitionHash ([]byte)`

* `ChainID (string)`

* `ProviderAddress ([]byte)`

* `ServiceLevel (string)`

* `ServicePricing (string)`

* `BindingExpiration (int64)`

* `IsValid (enum)`: `True` 또는 `False`

**서비스 요청(Service Invocation)**

![서비스 요청 도안](https://github.com/irisnet/irisnet/blob/master/images/chap2-3.png?raw=true)

소비자와 서비스 제공자는 서로 *엔드포인트*를 통해 소통한다. 엔드포인트는 *요청 테이블(request table)* 과 *응답 테이블(response table)* 형태로 존재한다. 모든 서비스 요청은 요청 테이블에 합산되며, 서비스 제공자들은 이 테이블을 모니터링 할 수 있다. 서비스 제공자는 요청 테이블에 올라온 서비스 요청 중 본인이 대상인 것을 처리하고, 이후 결과(또는 에러)를 응답 테이블에 합산한다. 소비자는 이 응답 테이블을 모니터링 한다.

`Multicast` 서비스의 경우, 모든 바인딩은 하나의 요청테이블을 공유한다. `Unicast` 서비스의 경우 각 바인딩 별로 새로운 요청 테이블이 생산되고 유지되며, 각 소비자 별로 다른 응답 테이블이 생성되고 유지된다.

`ServiceRequest`는 다음과 같은 값으로 구성된다:


* `ChainID (string)`: 소비자 연결되어있는 블록체인의 ID

* `ConsumerAddress ([]byte)`: 소비자의 블록체인 주소

* `DefinitionHash ([]byte)`: 서비스 정의의 해쉬값

* `MethodID (int)`: 호출하는 메소드의 ID

* `InputValue (string)`: 구조화된 인풋 값

* `BindingHash ([]byte)`: 타겟 바인딩의 해쉬 값 (`Unicast`인 경우 해당됨) *선택*

* `MaxServiceFee (int64)`: 특정 `Multicast`요청에 대해서 소비자가 지불 할 의사가 있는 최대 수수료 값 *선택*

* `Timeout (int)`: 소비자가 정의한 최대 응답 대기 기간(블록 수로 계산)

`PostServiceRequestTx` 트랜잭션은 다음과 같은 값으로 구성되어 있다:

* `Requests ([]ServiceRequest)`: 게시할 서비스 요청

* `RequestDeposits ([]int64)`: 소비자가 각 요청마다 예치해야하는 예치금(IRIS 토큰으로 계산). 이 값은 `MinRequestDeposit`에 정의되어있는 값 보다 높아야 한다. 이 요청 예치금(request deposit)은 서비스를 제공 받은 소비자가 해당 사실을 확인하는 것을 장려하기 위해 존재한다 (`ConfirmServiceResponseTx` 참고)

애플리케이션은 각 소비자 요청의 `ChainID` 와 `ConsumerAddress`, 바인딩 타켓의 유효성, 예치금 충족 여부, 소비자 잔고가 해당 서비스 예치금과 수수료를 지불할 수 있는지, 그리고 트랜잭션의 요청(request)수가 `MaxRequestPostBatch`에 정의된 값 보다 낮은지 검증한다.

서비스 요청이 검증된 후 요청 테이블에 게시된다. 이때 수수료(`Multicast` 요청의 경우 `MaxServiceFee`)는 소비자 잔고에서 공제되고 에스크로에 보관된다.

`GetServiceRequest` 쿼리(query)는 다음과 같은 값으로 구성된다:

* `DefinitionHash ([]byte)`: 서비스 정의의 해쉬값

* `BindingHash ([]byte)`: 특정 서비스 바인딩을 제공하는 서비스 제공자의 해쉬값. 애플리케이션은 해당 바인딩의 유효성을 확인하고 요청 값이 서비스 제공자의 `ChainID`와 `ProviderAddress`와 일치하는지 확인한다.

* `BeginHeight (uint64)`: 애플리케이션이 서비스 제공자에게 요청(request)을 전달하기 시작하는 블록 높이. `BatchSize`와 `MaxRequestBatch`의 값 중 작은 숫자로 처리된다.

* `BatchSize (int)`: 최대 요청 응답 수 

`ServiceResponse` 는 다음과 같은 값으로 구성된다:

* `RequestHash ([]byte)`: 매칭 된 요청의 해쉬값

* `BindingHash ([]byte)`: 제공자 서비스 바인딩의 해쉬값

* `OutputValue ([]byte)`: 구조화된 아웃풋 결과(output result). (상황에 따라 암호화될 수 있다) *선택*

* `ErrorMsg (string)`: 구조화된 에러 메시지 *선택*

`PostServiceResponseTx` 트랜잭션은 다음과 같은 값으로 구성된다:

* `Responses ([]ServiceResponse)`: 응답 테이블에 게시할 서비스 응답

애플리케이션은 모든 응답의 `ChainID`와 `ProviderAddress`가 서비스 제공자의 정보와 일치하는지 그리고 트랜잭션의 응답수가 `MaxResponsePostBatch`의 값 보다 낮은지 검증한다. 검증된 요청은 소비자에게 전달되기 위해 응답 테이블에 게시된다.

`GetServiceResponse` 쿼리(Query)는 다음과 같은 값으로 구성된다:

* `RequestHash ([]byte)`: 기존 요청(original request)의 해쉬값. 애플리케이션은 쿼리 요청자가 기존 요청의 `ChainID`와 `ConsumerAddress`가 동일한지 검증한다.

* `BeginHeight (uint64)`: 애플리케이션이 소비자에게 요청(request)을 전달하기 시작하는 블록 높이. `BatchSize`와 `MaxResponseGetBatch` 값 중 작은 숫자로 처리된다.

* `BatchSize (int)`: 최대 요청 응답 수

`ConfirmServiceResponseTx` 트랜잭션은 다음과 같은 값으루 구성된다:

* `ResponseHash ([][]byte)`: 확인할 요청(response)의 해쉬값

애플리케이션은 `ConfirmServiceResponseTx`를 요청한 유저가 확인 대상 요청(response)을 생성한 유저인지 확인하며, 트랜잭션의 요청 수가 `MaxResponseConfirmBatch`의 값 보다 낮은지를 검증한다.

`Timeout`에 지정된 값 밖(`Multicast` 요청의 경우 추가적인 요청이 들어오며 `MaxServiceFee`가 소진된 경우)의 요청은 애플리케이션이 거절한다. `Unicast`요청을 받은 소비자는 요청을 받은 즉시 처리를 작한다. 반면, `Multicast`의 경우 소비자는 전달 받은 요청을 처리하기 전에 `Timeout` 기간이 만료될 때까지 기다려야 한다.

소비자가 `Unicast` 요청을 확인하는 경우, 서비스 비용는 소량의 수수료(해당 수수료는 `ServiceFeeTaxRate`에서 정의된다)를 공제한 후 에스크로에서 풀려 *시스템 리저브(system reserve)* 에 추가된다. 해당 요청에 연관이 있는 예치금은 소비자에게 반납된다.

반면 `Multicast`의 경우는 조금 더 상황이 복잡하다. 특정 요청이 확인될 경우, `MaxServiceFee`와 해당 요청에 대한 서비스 비용에 비례하는 예치금의 일부만 소비자에게 반납된다. 만약 모든 요청이 확인된다면 에스크로에 보관되어있는 잔고가 소비자에게 반납된다.

만약 요청이 특정 응답 없이 꾸준한 타임아웃(timeout)을 한다면, 애플리케이션은 에스크로에 남아있는 잔고와 요청 예치금을 전부 소비자에게 돌려준다. 하지만 만약 소비자가 특정 응답을 지정된(`ResponseConfirmTimeout` + 응답 전송 당시의 블록체인 높이를 더한 값) 기간안에 확인하지 않는다면 `ResponseConfirmDelayPenaltyRate`에 명시된 소량의 벌금을 지불하게 된다. 벌금을 제외한 예치금은 소비자에게 환불되고, 관련 서비스 비용은 서비스 제공자에게 정상적으로 지급된다.

**분쟁 해결**

만약 특정 소비자가 서비스 응답에 대한 불만이 있을경우, 소비자는 중앙화된 기관 또는 법적 시스템에 의존하지 않고도 문제를 제기하고 해당 문제에 대한 타당한 응대를 받을 메커니즘이 필요하다. 이런 분쟁 해결 메커니즘에서 주관적인 판단이 있을 경우 악용될 확률이 있기때문에 객관적인 판단을 기반으로 해결을 해야할 필요가 있다.

아이리스 네트워크의 분쟁 해결 절차는 서비스 요청(service invocation) 절차와 유사한 형태를 가진다. 다만 기존 서비스 요청 절차와 달리 소비자는 서비스 제공자에게 `Complaint`를 보내고, 서비스 제공자는 `Resolution`으로 응답한다. 분쟁해결 절차의 인터랙션은 *컴플레인 테이블(complaint table)* 과 *해결책 테이블(resolution table)* 이라는 글로벌 엔드포인트(endpoint)를 통해 이루어진다.

현재 아이리스 네트워크의 디자인에 따르면, 소비자는 문제를 제기할때 일정의 예치금을 입금해야 한다. 소비자가 서비스 제공자가 응답한 해결책을 확인하지 않는 경우, 해당 예치금의 일부는 벌금으로 과금된다.  이는 소비자가 응답이 완료된 해결책을 확인(confirm)하지 않는 것을 방지하기 위함이다. 지정된 기간 내에 소비자의 문제에 대해 응답하지 않는 서비스 제공자 또한 위와 비슷하게 슬래싱을 당할 수 있다.

`Complaint`는 다음과 같은 값으로 구성된다:

* `ResponseHash ([]byte)`: 분쟁 대상인 응답(response)의 해쉬값

* `Problem (string)`: 서비스 제공자의 응답에 대한 불만의 설명

* `PreferredDisposal (enum)`: `Refund` 또는 `Redo`

`Resolution` 은 다음과 같은 값으로 구성된다: 

* `ComplaintHash ([]byte)`: 응답하는 분쟁 `Complaint`의 해쉬값

* `Disposal (enum)`: `Refund` 또는 `Redo`

* `Refund (uint64)`: 환불할 서비스 비용의 값 *선택*

* `OutputValue ([]byte)`: 구조화된 아웃풋 결과(output result). (상황에 따라 암호화될 수 있다) *선택*

위에 설명된 분쟁 해결 절차는 법적 유효성을 가지지 않을 수 있다. 하지만 아이리스는 이런 절차가 가장 흔한 분쟁에 대한 해결책을 제시할 수 있을 것이라고 생각한다.

**서비스 프로파일링**

iService 생태계를 구축하는데에는 몇가지 문제점들이 있따. 가장 큰 문제 중 하나는 소비자들이 적합한 서비스 제공자를 찾는 것이다. 소비자는 서비스를 선택하기 위해서 서비스 제공자들의 성능 지표를 원하지만, 소비자 사용률이 저조한 경우 서비스 제공자에 대한 데이터 부족으로 성능 지표가 제공될 수 없을 수 있다.

이런 원형된 문제를 해결하는 의도에서, 아이리스 네트워크는 특수 상위 권한을 보유한 시스템 유저를 통해 프로파일링 메커니즘을 소개하려 한다. *프로파일러(Profiler)* 는 특정 기간마다 활성화된 모든 서비스에 요청을 하고 관련 정보를 기록한다. 프로파일러는 기록된 데이터를 토대로 서비스 제공자에 대한 객관적인 성능 지표(응답 속도, 사용 가능성(availability), 분쟁 처리 등)를 소비자에게 제공하는 역할을 한다.

소비자의 서비스 요청과는 달리, 서비스 프로파일링 요청은 서비스 비용과 예치금에서 면제되지만 네트워크 사용료는 지불해야 한다. 이런 프로파일링 요청은 지정된 특정 주소에서만 발생하며, 애플리케이션은 이를 인지하여 처리를 한다.

프로파일링 활동은 신규 서비스에 대해서 규칙적이게 발생하며, 이후 소비자 사용률이 높아지는 서비스는 실제 소비자 데이터 기반으로 성능 지표를 제공하여 프로파일링 활동이 줄어들게 한다. 

프로파일링 활동에서 발생하는 네트워크 수수료(transaction fees)는 기본적으로 시스템의 예치금에서 지급되며, 추후 필요에 따라 재단이 개입할 수 있다.

**쿼리(Query)**

상단에 설명된 모든 서비스는 ABCI의 쿼리 인터페이스(query interface)[\[3\]][3]를 통해 요청될 수 있다. 이런 쿼리들은 *쿼리 연결(Query connection)* 을 통해서 이루어지며, 합의 프로세스에 참가하지 않는다. 상단에 `GetServiceRequest` 과 `GetServiceResponse` 같은 쿼리들이 작동하는지 설명되어있다.

다음은 (포괄적이지 않은) 쿼리들에 대한 요약이다 Below is a non-exhaustive summary of our currently planned queries:

**서비스 오브젝트(Service object)**

| 오브젝트                               | 흔히 이용되는 필터            | 권한                        |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| 서비스 정의(service definition)                       | Name, keywords, source (chain ID), messaging type, with active bindings... | 모두 가능                         |
| (특정 정의에 대한) 서비스 바인딩 | Location (local or remote), pricing, service level, expiration... | 모두 가능                         |
| 서비스 요청(service request)                          | Service definition and binding, blockchain height, batch size | 요청 관계자 |
| 서비스 응답(service response)                         | Service request, blockchain height, batch size | 요청/응답 관련 소비자                    |


**성능 지표**

| 분야                    | 지표                              | 권한 |
| --------------------------- | ---------------------------------------- | ----------------- |
| 서비스 제공자 (주소)          | 서비스 제공 횟수 (과거/현재 제공중), 응답 시간 (최소, 최대, 평균), 처리된 요청 (로컬, 원격), 미처리 요청 , 받은 컴플레인, 무시한 컴플레인, ... | 모두 가능  |
| 서비스 제공자 (바인딩)          | 활성화 시간, 응답 시간 (최소, 최대, 평균), 처리된 요청 (로컬, 원격), 미처리 요청, 받은 컴플레인, 무시한 컴플레인, ... | 모두 가능  |
| 소비자          | 서비스 이용 횟수, 요청 횟수, 확인한 요청 (확인 기간 내 / 확인 기간 초과), 요청한 컴플레인, 확인한 해결책(resolution), ... | 모두 가능  |
| 소비자 (서비스, 바인딩) | 요청 횟수, 확인한 요청 (확인 기간 내 / 확인 기간 초과), 요청한 컴플레인, 확인한 해결책(resolution), ... | 모두 가능  |


### IBC 확장

아이리스 네트워크가 코스모스를 기반으로 서비스 인프라를 제공하는 것의 가장 큰 장점 중 하나는 *요청과 전개*가 생태계 내에 있는 '블록체인의 인터넷'에서 가능하다는 것이다. 아이리스의 계획은 다음과 같다.

1. 서비스 정의는 아이리스 네트워크에 있는 모든 존에 전파된다;

2. 글로벌 서비스 바인딩은 아이리스 네트워크에 있는 모든 존에 전파된다;

3. 특정 원격 서비스 제공자가 대상인 서비스 요청과 컴플레인은 해당 서비스 제공자가 연결되어있는 블록체인으로 라우팅된다;

4. 특정 원격 소비자가 대상인 응답과 해결책(resolution)은 해당 소비자가 연결되어있는 블록체인으로 라우팅된다;

애플리케이션은 `CreateServiceDefinitionTx`를 처리하는 과정에서 이웃 체인들에 대한 정보가 포함된 `IBCPacket`을 생성하기 전에 `ServiceDefinition` 오브젝트를 먼저 검증하고 로컬 환경에 저장하도록 설계되어있다.

각 이웃 체인은 릴레이 과정에서 해당 패킷이 포함된 `IBCPacketTx` 를 전달받게 된다. 만약 `IBCPacketTx`를 전달받은 체인에 전달 받은 서비스 정의가 포함되지 않은 상태인 경우, 수신자 체인은 새로 `IBCPacket`을 생성해 `IBCPacketTx`를 전달받은 체인을 제외한 다른 체인에게 새로 생성한 `IBCPacket` 을 전달한다. 만약 서비스 정의가 수신자 체인에 존재하는 경우, 수신자 체인은 서비스 정의를 전파하지 않는다.

위와 비슷하게 `ServiceBinding`의`BindingType`이 `Global`로 설정되어 생성되었거나 기존 `Local`에서 `Global`로 변경된 경우, 해당 바인딩이 포함된 `IBCPacket`이 각 이웃 체인 대상으로 만들어지고 아이리스 네트워크를 통해서 모든 체인에 전파된다. 

위에 설명된 `IBCPacket`은 다음과 같은 값으로 구성된다:

* `Header (IBCPacketHeader)`: 패킷 헤더

* `Payload (ServiceDefinition or ServiceBinding)`: 서비스 정의 또는 서비스 바인딩의 바이트(byte)

`IBCPacketHeader`은 다음과 같은 값으로 구성되어있다:

* `SrcChainID (string)`: 해당 패킷을 생성하는 블록체인의 ID

* `DstChainID (string)`: 해당 패킷의 도착할 블록체인의 이웃 체인 ID

* `Number (int)`: 모든 패킷에 대한 고유 번호

* `Status (enum)`: `NoAck`

* `Type (string)`: "iris-service-definition" 또는 "iris-service-binding"

하단에서는 인터체인 서비스 요청이 어떻게 IBC를 통해 이루어지는지에 대한 설명이다. 

`Unicast` 서비스 요청이 발생하는 경우, 애플리케이션은 타겟 바인딩이 `Local`인지 확인을 한다. 만약 `Local`이 맞는 경우, `ServiceRequest`는 상단 2.2절에서 설명된 요청 테이블에 추가가 된다. 하지만 만약 `Local`이 아닌 경우, `ServiceRequest`가 포함된`IBCPacket`이 별도로 생성된다. 

`ServiceRequest`는 다음과 같은 값으로 구성된다: 

* `Header (IBCPacketHeader)`: 패킷 헤더

* `Payload (ServiceRequest)`: 서비스 요청의 바이트(byte)

상단의 `IBCPacketHeader`는 다음과 같은 값으로 구성된다:

* `SrcChainID (string)`: 해당 패킷을 생성하는 체인의 ID

* `DstChainID (string)`: 원격 서비스 제공자가 연결되어있는 블록체인의 ID (예시, `ServiceRequest.ServiceBinding.ChainID`)

* `Number (int)`: 모든 패킷의 고유 번호

* `Status (enum)`: `AckPending`

* `Type (string)`: "iris-service-request"

* `MaxHeight (int)`: 현재 블록높이 + `ServiceRequest.Timeout`값

원격 요청이 목적지 체인에 도착하는 경우, 애플리케이션은 타겟 바인딩을 위해 해당되는 엔드포인트(요청 테이블)에 해당 요청(request)를 추가한다. 이 원격 요청에 대한 확인은 `IBCPacket` 형태의 확인서를 통해 요청이 시작된 체인으로 돌아가 해당 체인의 엔드포인트(여기의 경우 응답 테이블)에 추가되어 요청한 소비자에게 돌아간다.

`Multicast` 서비스는 기존 `Unicast` 서비스의 이동 형태와 비슷하지만, 요청이 시작된 체인에서 1개 이상의 `IBCPacket`이 생성된다는 점에서 다르다.

원격 컴플레인(complaint)과 해결책(resolution)은 기존 요청-응답 형태와 동일하기 때문에 설명을 생략한다.

다음은 모든 애플리케이션-의존(application-dependent) `IBCPacket` 종류다:

| **종류**                  | **iService 오브젝트** |
| ------------------------- | ------------------- |
| "iris-service-definition" | 서비스 정의(ServiceDefinition)   |
| "iris-service-binding"    | 서비스 바인딩(ServiceBinding)      |
| "iris-service-request"    | 서비스 요청(ServiceRequest)      |
| "iris-service-response"   | 서비스 응답(ServiceResponse)     |
| "iris-complaint"          | 컴플레인(Complaint)           |
| "iris-resolution"         | 해결책(Resolution)          |

<div STYLE="page-break-after: always;"></div>

## 이용 사례 ################################################################

다음 부분에서는 아이리스 네트워크의 이용 사례에 대해서 설명한다.

### 프라이버시 보호 데이터 분석을 위한 분산화 AI

우리가 여기에 제시하는 서비스는 상하이 기반 스타트엄 Bianjie AI가 프로토타이핑을 진행한 서비스 인프라다. 현재 Bianjie AI는 이 서비스를 `BEAN (Blockchain Edge Analytics Network)`에 응용하여 분석 모델을 위한 데이터 부족 문제를 해결하려고 한다. 동종적 암호화(homomorphic encryption)은 암호화된 데이터에 대한 연산을 가능하게 하는 방법 중 하나이지만, 느린 속도 때문에 현실적인 머신러닝 문제를 해결하는데에 한계가 있다.

BEAN은 이런 문제를 조금 다른 형식으로 풀어나가기 위해 만들어졌다. BEAN은 기존 분산화 AI 연구 자료[\[14\]][14]가 제시하는 모델 평행화(model parallelism)와 서비스 지향 아키텍처(SOA) 디자인을 결합하여 분산화 분석 서비스를 블록체인 상위 계층으로 도입하는 방식이다.

데이터 접근성 문제를 해결하기 위해 데이터 부분에서 운용되는 (부분적) 모델은 오픈소스화 되어 특정 서비스 정의로 소비자에게 제공되어야 한다. 소비자는 부분적 모델에만 접근할 수 있기 때문에, 모델 개발자는 누군가 본인들의 분석 모델을 도용할 수 있다는 걱정을 할 필요가 없게된다. 이와 동일하게 데이터 제공자는 본인들의 소유권을 떠나지 않기 때문에 데이터 접근성을 관리하기 수월해진다.

이 외에 장점은 다음과 같다:
1. 파라메트릭 데이터의 일부분만 블록체인에서 교환되기 때문에 성능에 향상에 도움을 줄 수 있다
2. 데이터 사용 감사(audit)이 실용적이다 (의료 분야에서 필요한 부분 중 하나) 

의료 데이터에서 프라이버시는 가장 중요한 것 중에 하나이다. 그렇기 때문에, 수많은 필수 보안 요소들이 적용되어있다. 이런 보안적 요소 때문에 의료기관 간의 협력(병원 간 진료 기록 공유, 다기관 임상실험 참여자 자료 공유, 보험 청구 자동화)을 위해 의료 정보 데이터를 공유하는 것이 쉽지가 않다. 이 의료데이터 서비스 계층의 최소기능제품(MVP, Minimum Viable Product)은 `Ethermint`를 이용해 다수의 병원, 보험 회사, 그리고 데이터 분석 회사를 의료 데이터의 프라이버시를 보존하면서 연결할 수 있도록 한다. 온체인 서비스 등록과 호출(invocation)은 스마트 컨트랙트를 이용해 될 수 있다.

이런 서비스 계층을 이용한 오프체인 데이터 처리의 예시 중 하나는 '진단 관련 그룹(DRG, Diagnosis Related Group)' 분석 서비스이다. 예를 들어, 특정 병원이 DRG 서비스를 호출하게 되면, 요청된 의료정보는 서비스 제공자가 제공한 소비자 NLP 클라인언트(예를 들어 SQL/파이썬 기반 NLP)를 통해 필요한 부분만 전달이 될수 있다. 전달되는 DRG 데이터는 서비스 제공자의 원칙에 따라 오프체인에서 처리가 될수 있으며 개인 프라이버시를 보존하는 형태로 처리될 수 있다. 

`BEAN`의 경우 위에 있는 사례 외에도 분산화 분석(distributed analytics), 서비스 제공자와 서비스 소비자의 연결, 안전한 거래 장부 기록, 분산 컴퓨팅 등 다양한 분야에서 이용될 수 있을 것으로 기대되고 있다.

### 데이터 분석 거래소

다수의 AI+블록체인 서비스를 분석한 결과, 대다수의 프로젝트는 데이터 거래소와 분석 API 거래소를 제공할 것을 염두하고 있다. `IRIS`의 인프라의 경우, 데이터 서비를 이용해 데이터 공유 서비스를 제공할 수 있고 `IRIS` 서비스 제공자 SDK를 이용해 래핑 분석 API(wrapping analytics API)를 쉽게 구현할 수 있다.

### 분산화 전자상거래

`IRIS` 인프라를 이용한다면 `ERP` 같은 기존 인벤토리 정보를 이용하거나 신뢰될 수 있는 데이터 소스의 인터체인 쿼리(query)를 하는 것은 기존 엔터프라이즈 애플리케이션 환경과 유사하게 구축할 수 있다. 이런 환경은 기존 애플리케이션 개발자들에게 큰 장점으로 작용될 수 있을 것으로 기대된다. 아이리스 네트워크 환경을 이용한다면 아마존이나 알리바바 같은 기존 중앙화 전자상거래 시스템과 유사한 분산화 전자상거래 시스템을 구축할 수 있을 것이다.

### 퍼블릭 블록체인과 컨소시엄 블록체인의 결합

다수의 비즈니스 시나리오를 고려한다면 컨소시엄 블록체인과 퍼블릭 블록체인의 각 강점을 결합한 하이브리드 아키텍처를 이용하는 것이 큰 강점일 수 있다. 이런 시스템은 높은 성능, 우수 보안 그리고 경제적 인센티브를 제공하기 때문이다.

예를 들어, 병원과 보험사는 다수의 의료 보험 거래를 처리할 수 있는 성능의 컨소시엄 구축할 수 있다. 추가적으로 공유될 수 있는 특정 정보는 퍼블릭 블록체인으로 공유하여 특정 질병에 대한 통계를 공유하거나 글로벌 서비스 구축에 이용할 수 있을 것으로 기대된다. 또한 퍼블릭 블록체인에서 발생하는 경제적 인센티브는 기존 데이터를 제공하는 컨소시엄 블록체인 참여자에게 분배되어 서비스 품질을 높이는데 기여될 수 있다.

`IRIS`가 제공하는 인프라를 이용한다면 블록체인 시스템의 고질적인 성능, 보안, 개인정보 보호 측면의 단점을 가지지 않고도 대량의 자발적 공동 작업이 이루어질 수 있을 것이다.

`IRIS` 서비스 인프라는 이 외에도 자산 기반 보안 시스템(asset based security system), 분산화 규제 기술, 공제 시스템 등 다양한 측면에서 이용될 수 있을 것으로 기대된다. 아이리스 프로젝트는 앞으로 수 많은 애플리케이션 프로젝트들과 협력하여 그들이 생각하는 비즈니스 가치를 블록체인 인프라를 통해 더 효율적으로 구축할 수 있도록 지원할 예정이다.

<div STYLE="page-break-after: always;"></div>

## 토큰경제학 ################################################################

아이리스 네트워크는 코스모스 네트워크와 같이 멀티 토큰 모델을 지원할 수 있도록 설계되었다. 생태계 내에 있는 토큰들은 다른 존에서 보관이 가능하며, 아이리스 허브를 통해서 존 간 이동이 가능하다.

현재 아이리스 네트워크의 운영에서 이용될 토큰은 두가지가 있다:

* 스테이킹 토큰
* 수수료 토큰

### 스테이킹 토큰

아이리스 네트워크는 코스모스 네트워크의 스테이킹 메커니즘 디자인을 응용한 고유 스테이킹 토큰을 이용한다. 이 토큰의 명칭은 `IRIS`다. 현재로써 IRIS 토큰의 기능은 다음과 같다:

* 검증인(validator)과 위임자(delegator)를 기반으로 설계된 아이리스 네트워크의 합의 기능

* 아이리스 네트워크 거버넌스의 투표권을 부여하는 기능


### 수수료 토큰

아이리스 네트워크에는 두가지 수수료 토큰이 존재한다:



* **네트워크 수수료** 이 토큰은 스팸 방지 용도와 원장을 관리하는 밸리데이터에게 경제적 인센티브로 지급되는 용도


* **서비스 수수료** 이 토큰은 아이리스 네트워크의 iService를 제공하는 서비스 제공자들에게 지급되는 용도로 이용된다. 아이리스 네트워크의 기본 결제용 토큰이다.

아이리스 네트워크는 코스모스 네트워크의 화이트리스트에 포함된 모든 토큰(예, [포톤](https://blog.cosmos.network/cosmos-fee-token-introducing-the-photon-8a62b2f51aa)]과 IRIS 토큰을 지원할 예정이다

아이리스 네트워크는 코스모스 네트워크 화이트리스트에 포함된 모든 토큰을 지원함으로써 네트워크 참여자들에게 더욱 편리한 환경을 제공할 수 있다. 코스모스의 `network fee token`의 경우, 각 밸리데이터는 config 파일에 본인이 각 수수료 토큰에 대한 가치를 정의한다. 원한다면 크론(cron) 프로세스를 활용하여 본인이 선택한 실시간 가격 데이터를 기반으로 수수료 토큰에 대한 가치를 지정할 수도 있다.

아이리스 네트워크는 `service fee token` 설계 또한 비슷한 멀티토큰 모델이 지원될 예정이다. 서비스 제공자는 본인이 원하는 토큰으로 서비스 비용을 지불받을 권리가 있으며, 이를 각자의 화이트리스트를 통해 지정할 수 있다.

아이리스 네트워크 참가자가 암호화폐 가격 변동성에 노출되는 확률을 낮추기 위해 아이래스 재단은 다양한 거래소에서 가격 데이터를 실시간으로 제공하는 iService를 제공할 수 있으며, 일종의 '오라클(oracle)' 서비스를 추후에 출시 할수 있다.

스테이킹 토큰과 수수료 토큰의 기능과 디자인은 법적 규제 준수 여부에 따라 추후에 변경될 수 있다.

<div STYLE="page-break-after: always;"></div>

## 초기 토큰 분배 ################################################################

제네시스에서 총 2,000,000,000개의 IRIS 토큰이 생성된다.  IRIS 토큰의 분배는 다음과 같이 예정되어있다:

* **프라이빗 세일**: 25%

* **Bianjie 개발팀**: 15% (4년에 걸쳐서 매월 1/48이 언락)


* **텐더민트 개발팀**: 10% (2년에 걸쳐서 매월 1/24이 언락)

* **아이리스 재단**: 15% (아이리스 재단 운영을 위해 보유)

* **생태계 개발**: 30% (아이리스 허브에 연결되는 존과 토큰 스왑; 잠재적 사용자 후원; 우수 파트너 지원; 퍼블릭 세일 가능성 있음)

* **ATOM 보유자 에어드랍**: 5% (코스모스 허브 월렛을 이용해 ATOM 보유자 대상 에어드랍. 에어드랍은 1년에 걸쳐서 매월 총 에어드랍 개수의 1/12가 분배)

아이리스 네트워크가 완성될 경우, IRIS 토큰의 연 인플레이션은 자발적으로 합의에 참가하기위해 스테이킹 되었다는 것을 고려해서 유동적이게 변경될 예정.

IRIS의 프라이빗 세일로 받은 수익금은 아이리스 네트워크 개발을 위해 다음과 같이 이용될 예정이다:

* **재단 운영비**: 10% (서비스 제공자, 법적 자문, 컨설팅, 감사 같은 외부 서비스 비용 포함)

* **소프트웨어 개발비**: 50% (메인넷 개발과 직접적으로 연관된 비용)

* **개발 지원**: 10% (해커톤 지원, 봉사자 지원, 교육 훈련 프로그램 등)

* **R&D 지원**: 10% (컨퍼런스, 연구 프로그램, 대학 활동)

* **마케팅 및 홍보**: 20% (사업 개발, 커뮤니티 프로그램, 여행비, 홍보, 출판, 등에 필요한 비용)

<div STYLE="page-break-after: always;"></div>

## 로드맵 ################################################################

아이리스 프로젝트의 계획은 다음과 같다. 이 정보는 예측성 지표이며 언제나 변경이 가능하다.

* **판구(PANGU)** (2019년 1월 \~ 2019년 3월) 아이리스 프로젝트의 첫 단계는 아이리스 허브 운영에 집중된다. 아이리스는 아이리스 네트워크 모바일 클라이언트를 공개할 예정이다. 이 단계에서 아이리스 프로젝트는 서비스 정의, 서비스 바인딩, 서비스 요청, 쿼리 같은 아이리스의 서비스 계층의 기초를 개발하는데 집중한다. 이 단계에서는 약 1-2개의 파트너사를 통해 iService를 공개할 예정이다.

* **누와(NUWA)** (2018년 4월 \~ 2019년 9월) 이 단계에서는 IRIS SDK의 베타 버전을 개발자들에게 공개할 계획이다. 추가적으로 IRISnet 모바일 클라이언트에서 iService 기능을 지원할 수 있도록 업그레이드 될 예정이다. 다양한 애플리케이션 특화 블록체인들과 협력하여 아이리스 허브의 존으로 연결될 수 있게 지원하고 코스모스 허브와 연결될 계획을 추진할 예정이다. 
 
* **쿠아푸(KUAFU)** (2019년 10월 \~ 2019년 12월) 세번째 단계는 아이리스 네트워크의 거버넌스 기능을 지원하기 위한 순차적 업그레이드에 집중할 예정이다.

* **호우이(HOUYI)** (2020년 이후)
네변째 단계에서는 아이리스 네트워크를 더욱 혁신적이게 만들 수 있는 기술 개발에 집중할 예정이다. 이 외에도 개발자 지원 활동을 늘리고 IRIS SDK와 모바일 클라이언트의 기능과 성능을 개선할 예정이다.

<div STYLE="page-break-after: always;"></div>

## 팀 ################################################################

**Bianjie**는 아이리스 네트워크의 코어 개발팀이다. 2016년에 상하이의 스타트업으로 설립된 [Bianjie](https://www.bianjie.ai) 팀은 분산화 애플리케이션 개발에 오랜 경력을 자랑한다. Bianjie는 의료 기관과 금융 기관에 AI와 블록체인 기술을 적용한 혁신적인 제품과 솔루션을 제공하는데 집중해왔다. Bianjie는 아이리스 외에도 `BEAN (Blockchain Edge Analytics Network)`라는 코어 제품을 개발중이다. BEAN은 의료 데이터 분석 서비스를 제공하는 허가형 블록체인으로, 자연어처리, 머신러닝 같은 기술을 응용해 프라이버시를 보존하는 의료 데이터 분석을 제공한다. **Bianjie**는 코스모스 네트워크의 중국 서비스/운영 파트너이다.

**텐더민트** ([Tendermint](https://www.tendermint.com) 합의 알고리즘을 개발하고 현재 코스모스를 제작중에 있음), **Wancloud** ([Wanxiang
Blockchain](http://www.wxblockchain.com)의 계열사 등이 현재 **Bianjie AI**와 함께 기술적 파트너로 아이리스 네트워크의 인프라를 개발하고 있다.

텐더민트는 아이리스 프로젝트 팀에게 기술적 고문과 개발 지원을 제공하여 아이리스 프로젝트를 통해 텐더민트 ABCI와 코스모스 IBC 활용도를 높히는데 지원하고 있다.
[Wancloud](https://www.wancloud.io)는 코스모스와 아이리스 생태계의 전략적 파트너로써 아시아 지역의 코스모스/아이리스 개발을 지원하고 있다.

### 핵심 멤버

**Haifeng Xi**

[Haifeng](https://www.linkedin.com/in/haifengxi/)은 시니어 기술자이자 사업가다. 그는 University of Maryland에서 전자컴퓨터공학 석사 학위를 취득했다. 아이리스 네트워크를 시작하기 전에 Haifeng은 Wanxiang Blockchain의 Wancloud에서 CTO를 했으며, 그 외에도 미국 금융 기업 Tudor Investment와 RBS Sempra에서 시니어 아키텍트, NASDAQ 상장기업을 포함한 3개의 중국 기업에서 CTO 직위를 역임했다.


**Harriet Cao**

[Harriet](https://www.linkedin.com/in/harrietcao/) 은 블록체인 기반 스마트 서비스와 분산화 AI 기술을 제공하는 상하이 기반 Bianjie AI의 창립자다. Harriet은 데이터 분석과 인공지능 기술에서 수차례 수상했으며, 2010 INFORMS Daniel H. Wageris Prize를 받기도 했다. Bianjie AI를 창립하기 전, 그는 IBM Research에서 16년 동안 일했으며, IBM Research Shanghai Lab의 디렉터, IBM Global Labs의 빅데이터 분석 리드 등의 역할을 맡았다. Harriet은 Carnegie Mellon University의 로보트공학 석사 학위와 칭화대학교의 자동화 컨트롤 석사 학위를 보유하고 있다.

**Jae Kwon**

2005년 코넬 대학교에서 졸업한 후, 재권은 다양한 실리콘 밸리 기업들(아마존, Yelp)에서 소프트웨어 개발자로 일했다. 이후 그는 블록체인 생태계에 빠지며 텐더민트 BFT 합의 알고리즘을 개발하였고, 이후 학술적 검증이 가능한 지분증명 알고리즘을 만들기 위해 텐더민트 코어 블록체인 엔진을 개발하였다. 재권은 코스모스의 창립자로써 현재 '블록체인의 인터넷'을 그리는 코스모스를 개발하고 있다.

**Tom Tao**

2016년에 Wanxiang에 합류한 [Tom](https://www.linkedin.com/in/tom-tao-14763a45/)은 Wanxiang Blockchain Group의 컨설팅 서비스, Wancloud BaaS 플랫폼과 ChainBase 액셀레레이터/인큐베이터 서비스를 담당하고 있다. Tom Tao는 Wanxiang을 합류하기 전에 세계적인 기업에서 서비스 관리와 비즈니스 매니지먼트 역할을 무려 18년 동안 했다. 그는 2013년 부터 클라우드 서비스, IoT 데이터 서비스 플랫폼, 그리고 액셀레레이터 프로그램을 중국 시장에 소개하며 기술적 트렌드를 빠르게 따라잡는 역할을 했다.

그는 Nankai University에서 전기공학 학사, 그리고 Fudan University에서 물리학 석사 학위를 수료했다.

### 어드바이저

**Dr. Shuo Bai**

Bai 박사는 현 ChainaLedger Technical Committee 위원장이자 전 상하이 증권 거래소의 총 아키텍트였다. 그는 중국 업계의 시니어 블록체인 전문가이며, Peking Univeristy에서 박사 학위를 수료한 후 학술, 연구, 개발 등의 전문 분야에서 활동을 했다. 또한 Chinese Academy of Sciences와 Institute of Computing Technology의 수석 과학자, 소프트웨어 개발 디렉터 등 고위 직위에서 일을했다. 그는 2000년 부터 China National Internet Emergency Center (CNCERT/CC) 설립을 주도하였다.

그는 학술적 이론 연구 외에도 금융 거래소, 컨소시엄 블록체인, 퍼블릭 블록체인 기술 분야에 전문성과 경험을 보유하고 있다.

**Jim Yang**

[Jim Yang](https://www.linkedin.com/in/jimyang/) 은 텐더민트에서 전략을 맡고있다. 모바일 메시징 스투디오 ChatX를 설립했으며, 그 외에도 레드햇(Red Hat)에 인수된 Identyx의 공동 설립자이자 대표를 역임했다. Identyx는 오픈소스 엔터프라이즈 신원 관리 소프트웨어다.

**Zaki Manian**

[Zaki Manian](https://zaki.manian.org), Trusted IoT Alliance 전무이사로써 블록체인과 암호화폐 기술에 큰 기여를 하고있다. 그는 암호학과 분산화 합의 시스템에 높은 전문성을 보유하고 있으며, 코스모스 프로젝트의 어드바이저 역할을 하고 있다.

**Adrian Brink**

[Adrian Brink](https://adrianbrink.com), 테조스, 코스모스, 폴카닷 등 다수의 지분증명 블록체인 시스템의 검증인을 운영하는 Cryptium Labs의 설립자다. 그는 과거 텐더민트와 코스모스에서 파트너십 디렉터와 코어 개발자로써 일했다.

**Michael Yuan**

[Dr. Michael Yuan](http://www.michaelyuan.com)는 [사이버마일즈 재단](https://cm.5miles.com)의 이사다. 그는 University of Texas at Austin 우주물리학 박사 학위를 수료했다. 지금까지 그는 무려 5개의 소프트웨어 개발 관련 책의 저자로써 Prentice Hall, Addison-Wesley 그리고 O'Reilly 같은 유명 출판사를 통해 출판되었다. Michael Yuan 박사는 파이어폭스, Fedora, JBoss 등 다수의 오픈소스 프로젝트에서 활동했으며, 모바일 및 엔터프라이즈 소프트웨어 전문가이다. 그는 미국 정부의 스폰서를 받은 다수의 연구 프로젝트를 이끌기도 했다.

[Yubo](https://www.linkedin.com/in/yubo-ruan/)는 IRISnet에 투자한 펀드 중 하나인 8 Decimal Capital의 창립자다. 8 Decimal Capital은 IRISnet 외에도 0x, Kyber, Ontology, Fcoin, Zilliqa, ICON, Wanchain, Bibox, BiShiJie 등 다수의 프로젝트에 투자했다. Yubo는 보스턴에 위치한 Skylight Investment의 공동 창립자이며, Skylight Investment는 뉴욕거래소에 상장된 New Oriental의 투자를 받기도 했다. 과거에 그는 Alisimba(TopHacker Group에 인수) 등 2개의 기업을 성공적으로 창립했으며, 4개의 특허를 보유하고 있다. 그는 2017 AACYF 30 under 30의 수상자이며, 2012년 iENA 국제 발명자 대회에서 은상을 수상했다.
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
