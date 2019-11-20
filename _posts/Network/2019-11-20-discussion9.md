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

time out을 왜 기다리지 않나요? timeout은 여유있게 잡기 때문에 기다리는 delay가 있다.
fast retransmit이란, loss가 났다는 것을 더 빨리 감지하고 retransmit을 할 수 있는 것임.


# 2. 왜 3-way handshake의 delay는 1.5RTT가 아닌 1RTT 밖에 걸리지 않나요?

3-way handshake의 마지막 ACK 전송에서부터 데이터 segment를 보내기 때문이다. (piggyback)

# 3. traffic intensity (p=La/R) 이 1에 가까워 질 수록 무슨 일이 일어날까요.

p(로우)가 분모 값이 커지기 때문에 무한대로 증가하게 된다.

* traffic intensity : 트래픽 혼잡도
* La/R -> 1 : average queueing 딜레이가 커진다.
* La/R > 1 : 처리량 보다 많이 도착하기 때문에 packet loss 발생. 비트가 큐에 도착하는 평균율이 비트가 큐에서 전송되는 비율을 초과

# 4. 다음 용어를 설명하세요 : congestion window, sending rate, bandwidth probing

* congestion window : ACK을 받기 전 까지 보낼 수 있는 데이터의 크기. 네트워크가 혼잡할 때 네트워크 혼잡도(=부하)를 감소시키기위해 사용하는 sender 측의 window. window size  만큼만 패킷을 보낸다.
* sending rate : 시간 당 보낼 수 있는 바이트 수. 전송률.
* bandwidth probing : congestion window 의 사이즈를 적절하게 조절하기 위해 찾아가는 과정.

# 5. TCP slow start가 의미하는게 무엇인지, 어떻게 사용되는지 설명하세요.

TCP slow start : sender 와 receiver 사이에 bandwidth이 작아 느린 라우터가 있다면, 중간 라우터는 반드시 패킷들을 큐잉해야한다. 그래서 TCP connection의 throughput을 급격하게 저하시킬 수 있다.
새로운 패킷들이 네트워크로 보내져야 할 시점에서 rate를 관찰하는데 상대편으로부터 acknowledgement가 되돌아온 시점으로 rate를 계산한다.

사용 방법 : Slow start는 또 하나의 window를 송신자의 TCP에 추가했다 : "cwnd"라고 불리는 congestion window가 바로 그것이다. 새로운 connection이 다른 네트워크에 있는 host와의 사이에서 맺어지면, congestion window가 1개의 segment로 초기화 된다. (segment size는 상대방으로부터 통보된 것이거나 디폴트 값이다. 디폴트 값은 보통 536이거나 512 이다). ACK가 도착할때마다, congestion window는 1개 segment씩 증가된다. 송신자는 congestion window와 수신자가 광고한 window size 중에서 작은값까지 데이터를 전송할 수 있다. Congestion window는 송신자에 의해서 수행되는 flow control이다. 반면에 광고된 window는 수신자에 의해서 수행되는 flow control이다. 전자는 송신자가 network의 congestion 상태를 평가하는 것을 기반으로 하고, 후자는 이 connection의 수신자의 가용한 buffer 공간과 관련이 있다. 
[출처] [오리뎅이의 TCP 이야기 - 8] 전혀 slow 하지 않은 Slow Start|작성자 오리뎅이

Slow Start 단계에서는 segment 1개를 보내고, ACK이 돌아오면 2개를 보내고, 또 ACK이 돌아오면 4개를 보내고 하는 식으로 한번에 보내는 데이터를 segment 갯수를 2배씩 증가시킴으로써 exponention하게 증가시켜 나갑니다.
[출처] [오리뎅이의 TCP 이야기 - 8] 전혀 slow 하지 않은 Slow Start|작성자 오리뎅이

