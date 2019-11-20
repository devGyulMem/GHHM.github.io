---
layout: post
title:  "네트워크 문제 9"
navigation: True
tags: [Network]
class: post-template
subtitle: "Discussion 9"
subclass: 'post tag-getting-started'
author: mem
---

# 1. TCP는 3개의 중복 ACK을 받으면 fast retransmit을 합니다. 처음 중복된 ACK을 왜 버리지 않나요? 왜 timeout을 기다리지 않나요?

처음 중복된 ack을 받았을 땐 packet loss인지 out of order 인지 판단할 수 없다.

* out of order 일 떄 duplicate ack
* premature timeout 일 때 duplicate ack

위의 두 가지 경우 까지 중복된 ack이 올 수 있지만 그 이상은 packet loss라고 판단할 수 있다.


# 2. 왜 3-way handshake의 delay는 1.5RTT가 아닌 1RTT 밖에 걸리지 않나요?

3-way handshake의 마지막 전송에서부터 데이터 segment를 보내기 때문이다.

# 3. traffic intensity (p=La/R) 이 1에 가까워 질 수록 무슨 일이 일어날까요

* traffic intensity : 트래픽 혼잡도
* La/R -> 1 : average queueing 딜레이가 커진다.
* La/R > 1 : 처리량 보다 많이 도착하기 때문에 packet loss 발생. 비트가 큐에 도착하는 평균율이 비트가 큐에서 전송되는 비율을 초과

# 4. 다음 용어를 설명하세요 : congestion window, sending rate, bandwidth probing

* congestion window : 네트워크가 혼잡할 때 네트워크 혼잡도(=부하)를 감소시키기위해 사용하는 sender 측의 window. window size  만큼만 패킷을 보낸다.
* sending rate : 전송률
* bandwidth probing : 

# 5. TCP slow start가 의미하는게 무엇인지, 어떻게 사용되는지 설명하세요.

TCP slow start : sender 와 receiver 사이에 bandwidth이 작아 느린 라우터가 있다면, 중간 라우터는 반드시 패킷들을 큐잉해야한다. 그래서 TCP connection의 throughput을 급격하게 저하시킬 수 있다.

새로운 패킷들이 네트워크로 보내져야 할 시점에서 rate를 관찰하는데 상대편으로부터 acknowledgement가 되돌아온 시점으로 rate를 계산한다.
