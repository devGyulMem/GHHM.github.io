---
layout: post
title:  "네트워크 문제 2"
navigation: True
tags: [Network]
class: post-template
subtitle: "Discussion 2"
subclass: 'post tag-getting-started'
author: mem
---


## 1. address aggregation (또는 route aggregation)을 설명하고 왜 longest prefix matching 이 중요한지 설명하세요

address aggregation : 각각의 IP 주소를 저장하는 것이 아니라, IP 주소의 범위를 지정하여 forwarding table 을 작성하게 한다.

longest prefix matching : Forwarding table에서 목적지 주소를 주었을 때 더 긴 주소와 맞는 인터페이스를 선택한다.
- 이렇게 하면 하나의 주소로 전체 서브넷에 방송이 가능하기 떄문. 즉 효율적인 광고가 가능하다.

- 만약 구매한 도메인이 이사를 하여 ISP 범위를 벗어나게 된다면 forwarding table에 도메인 주소만 간단히 추가하는 것으로 ISP 구역을 변경할 수 있다. longest prefix matching이기 떄문에 더 적은 범위의 주소를 따로 지정 가능하기 때문.

#### CAM (content addressable memory) 매우 속도를 요하는 탐색 프로그램에서 사용하는 특수한 메모리

메모리 공간 전체를 검색해서 검색어가 위치하고 있는 주소 및 데이터를 반환
<-> RAM 은 사용자가 메모리 주소를 주면 해당 주소의 데이터를 리턴함.

#### TCAM(Ternary CAM)
이진(Binary) CAM이 1과 0으로 이루어진 검색어만을 사용한다면, TCAM은 1과 0이외에 "X"(Don't care)를 허용하여, 검색에 보다 유연성을 제공한다. 예를 들어, TCAM이 "10XX0"으로 검색하면, "10000", "10010", "10100", "10110"의 네 개의 검색어에 대한 검색이 수행된다. 이러한 새로운 유연성은 추가적인 비용을 요구하는데 TCAM는 이진 CAM에 비해 "X"상태를 저장하기 위한 추가적인 메모리를 요구한다.
-위키백과

고속 라우터나 3계층 스위치에서 IP 주소 검색의 라우팅 테이블을 저장하기 위해 특별히 제작된 메모리. 입력된 패킷의 목적지 주소와, TCAM에 저장된 모든 엔트리의 프리픽스들이 동시에 비교되어, 일치하는 엔트리 중 가장 길게 일치하는 엔트리의 주소가 선택되며, 이 주소가 가리키는 포워딩 메모리에서 출력 포트 정보와 다음 홈 주소 정보가 얻어진다. 구현이 간편하고, 매우 빠른 성능을 보이지만 일반 정적 기억 장치(SRAM)에 비하여 면적을 크게 차지하고, 전력 소모가 커, 큰 라우팅 테이블이나 IPv6로의 확장에도 적합치 않은 단점이 있다.
[네이버 지식백과] TCAM [Ternary Content Addressable Memory] (IT용어사전, 한국정보통신기술협회)



## 2. NAT translation table이 하는 일을 설명하세요.

NAT (network address translation): 외부 ip 랑 상관없이 내부 로컬 네트워크만 고려하여 사용할 수 있게 함. 하나의 public (or external) 주소 안에 여러 개의 private (or internal) 주소를 사용할 수 있다. 

packet의 source ip address 와 destination ip address 를 WAN side address 와 LAN side address 로 변환 시키기 위한 테이블이다.

즉 NAT에서 나가는 패킷은 private address 를  public address 로, NAT로 들어오는 패킷은 public address를 private address로 바꿔준다.


## 3. IPv6 터널 예제에서, router B는 IPv6만 알아야할까요 IPv4/IPv6 둘 다 알아야 할까요?

(A Ipv6) - (B IPv6) - (C IPv4) - (D IPv4) - (E IPv6) - (F IPv6)

둘 다 알아야 한다.
C가 IPv4이기 때문에, IPv4가 이해할 수 있는 헤더를 붙여줘야한다.


## 4. SDN OpenFlow network가 있다. S2에 datagram이 도착했다고 가정하자

SDN : 소프트웨어로 통신 흐름을 관리하는 통신 네트워크

![Alt text](/assets/images/post/discussion2-SDN-openflow.png)

### 4-1. S2에 source IP address "203.21.1.2"의 데이터그램이 도착하면 차단한다. (Firewall)

| match               | action |
|---------------------|--------|
| IP Src = 203.21.1.2 | drop   |

### 4-2. port 1 에서 도착한 host h5 또는 h6의 목적지가 h1 또는 h2일 때 output port 2로 포워딩한다.

| match               | action |
|---------------------|--------|
|Ingress = port 1     | forward(2)   |
| IP Src = 10.3.\*.\* | |
| IP Dst = 10.1.\*.\* | |

