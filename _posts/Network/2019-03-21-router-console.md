---
layout: post
title:  "Router console"
navigation: True
tags: [Network]
class: post-template
subtitle: "user mode, global mode"
background: assets/images/katalonlogo.png 
subclass: 'post tag-getting-started'
author: mem
---

# Router console

0. 초기상태

console password 필요

1. 사용자모드 (user mode)

`Router > enable`

2. 관리자모드

- 명렁어가 제한적이다 : show ping debug
** show run (show running config) : 메모리를 볼 수 있다. (조작: spcae 1페이지, enter 1라인, tab 나가기)
** do 를 붙이면 관리자 모드 아닌 곳에서도 사용 가능 (e.g. do show run)
` Router# config`

3. 설정모드 (global mode, config mode)

` Router(config)# `

입력된 명령어가 아니더라도 broadcast 하지 않게함
` Router(config)# no ip domain-lookup`

- 0번 콘솔에 접속한다.
` Router(config)# line con 0`

- 콘솔 접속 비밀번호 설정
`Router(config-line)# password cisco`

`Router(config-line)# password cisco secret`

response message와 현제 입력하는 메시지가 겹치지 않게함 (라우터는 속도가 느려서 메시지를 받는데 오래걸림)
`Router(config-line)# logging synchronous`

일정 시간 조작이 없으면 화면보호기 상태가 되고 password를 입력해야함.
귀찮을때 화면보호기 동작 끄는 법. 숫자는 순서대로 minute, second
`Router (config-line)# exec-timeout 0 0`

* telnet

가상 터미널 (virtual termianl) 패스워드가 있으면 0~4까지 동시에 5명 이용 가능하다
`line vty 0 4`

* nvram startup
cisco 라우터에서 비휘발 메모리 non volatile ram 을 startup이라고 한다.

