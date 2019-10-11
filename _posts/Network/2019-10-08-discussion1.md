---
layout: post
title:  "네트워크 문제 1"
navigation: True
tags: [Network]
class: post-template
subtitle: "Discussion 1"
subclass: 'post tag-getting-started'
author: mem
---

## 1. 웹 브라우저에서 "www.google.com"를 입력했을 떄 DNS 작동 원리를 설명하세요.

먼저 DHCP를 통해서 local DNS 서버의 주소를 알아냅니다.

local DNS server -> root DNS server (.) -> TLD DNS server (.com) -> authoritative DNS server (google.com)


## 2. BitTorrent에서 rarest first와 optimistically unchoke가 무엇인지 설명하세요.

rarest first : rare한 file을 먼저 받게하여 네트워크 혼란을 줄인다. 

optimistically unchoke : 나에게 잘해준 사람에게만 잘해준다. 랜덤하게 선택하여 chunk를 준다. 그 후 속도가 더 빠른 사람에게 준다. 새로운 peer에게도 기회를 준다.


## 3. Router에서 data plane 과 control plane의 주요 기능을 설명하세요. (routing 과 forwarding을 비교해서 설명)
 
 data plane - forwarding(datagram이 input port에 도착하여 어떤 output port로 나갈지 결정하는 과정
 
 control plane - 각각의 라우터가 서로 interact하여 routing algorithm으로 forwarding하는 과정, 네크워크를 봐야함

 ## 4. 223.1.0.0/22 라는 서브넷이 있다. 
 
 ### 4-1. prefix는 무엇인가
 22

 ### 4-2. 사용가능한 host address의 갯수는?
 2^10-2

 ### 4-3. 223.1.1.16은 같은 서브넷에 있는가?
같은 서브넷

 ## 5. 현재 컴퓨터의 32-bit IP 주소는 무엇인가? 컴퓨터가 어떻게 DHCP를 통해 IP 주소를 배정받는지 설명하시오.
 4개의 메시지를 통해 배정받는다.

 호스트는 처음에 배정받은 ip가 없다.
따라서 아래의 메시지는 전부 Braodcast로 이루어진다.

 1. DHCP discover (host -> DHCP): DHCP 서버를 찾는 메시지. Broadcast
 2. DHCP offer (DHCP -> host): DHCP 서버 주소와 함께 사용가능한 IP 주소를 알려줌. Braodcast
 3. DHCP request (host -> DHCP): 어떤 IP 주소를 사용할지 알려줌. Broadcast
 4. DHCP ACK (DHCP -> host): IP주소 배정 완료. Braodcast