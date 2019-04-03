---
layout: post
current: post
title:  "Git - LF will be replaced by CRLF"
navigation: True
tags: [ErrorAndSolution]
class: post-template
subtitle: "CRLF will be LF"
background: assets/images/git.png
cover: assets/images/git.png
subclass: 'post tag-getting-started'
author: mem
---


## Problem

> warning: LF will be replaced by CRLF in ...

or

> warning: CRLF will be replaced by LF in ...

## Reason
맥/리눅스 개발자와 윈도우 개발자가 git으로 협업할 때 발생하는 문제 (Whiatspace error)

유닉스 시스템은 한 줄 끝이 LF(Line Feed)

윈도우에서는 줄 하나가 CR(Carriage Retur) 과 LF. CRLF 로 이루어짐

## Solution
자동변환 기능
> core. autocrlf

윈도우 사용의 경우 항상 변환이 실행되도록 함 (프로젝트에만 적용하고싶으면 --global 빼면 된다)
> git config --global core.autocrlf true

맥/리눅스는 LF > CRLF 의 변환을 원하지 않음
단방향 변환이 가능하다
> git config --global core.autocrlf true input

에러메시지를 끄고 작업하고싶을 경우
>git config --global core.safecrlf false


