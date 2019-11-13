---
layout: post
title:  "네트워크 문제 8"
navigation: True
tags: [Network]
class: post-template
subtitle: "Discussion 8"
subclass: 'post tag-getting-started'
author: mem
---

# 1. TCP sequence number 와 Ack sequence number는 어떻게 정해지나요?
TCP sequence number : byte stream number, 받은 ACK sequence number
ACK sequence number : 받은 sequence number + data bytes, 앞으로 sender가 보내야할 넘버


# 2. cumulative ack 과 delayed ack 을 설명하세요

cumulative ack (누적 응답) : 윈도우 사이즈를 두어 패킷을 한 번에 보내고, ACK number 이전의 패킷이 무사히 도착했다는 것을 보장한다.

delayed ACK : 500ms를 기다리고 다른 Segment가 안 오면 ACK를 보낸다.
데이터가 없이 ACK만 있는 패킷 전송을 피하기 위해(reduce ACK-only response)
데이터가 있는 패킷에 piggyback 한다.
만일 패킷이 순서에 벗어났다면 사용하지 않음.


# 3. TCP sender는 packet loss를 어떻게 감지하고 또 어떻게 복구하나요?

ACK이 도착하지 않으면 / NACK이 도착하면 retransmission

# 4. TCP는 SampleRTT 를 측정하는 동안은 retransmission을 무시합니다. 왜 그럴까요?


# 5. TCP는 3개의 중복 ACK을 받으면 fast retransmit을 합니다. 처음 중복된 ACK을 왜 버리지 않나요? 왜 timeout을 기다리지 않나요?

처음 중복된 ack을 받았을 땐 packet loss인지 out of order 인지 판단할 수 없다.

* out of order 일 떄 duplicate ack
* premature timeout 일 때 duplicate ack

위의 두 가지 경우 까지 중복된 ack이 올 수 있지만 그 이상은 packet loss라고 판단할 수 있다.