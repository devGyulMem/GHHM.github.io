---
layout: post
current: post
title:  "셀렉터에서 label 선택 안됨"
navigation: True
tags: [ErrorAndSolution, Katalon Studio]
class: post-template
subtitle: "Unable to select option by label katalon"
subclass: 'post tag-getting-started'
author: mem
---

# Error

오류 메시지
`Unable to select option by label katalon`

`WebUI.selectOptionByLabel()` 로 선택할 때 선택 안되는 오류

# Reason

두 개의 spinner가 같은 td에 속해있을 시 생기는 문제

# Solution

katalon은 첫 번째 셀렉터의 xpath:idRelative를 

`//td/select`

이렇게 잡고

두 번째 셀렉터를

`//td[2]/select`

이렇게 잡는다..

첫 번째 셀렉터로 verify 검사를 해봤을 때 td를 포함하는 모든 `td[1],td[2],td[3]...` 의 셀렉터, 즉 여러 개의 element를 잡는다.

원래라면 여러 개의 element가 잡힐 경우, 첫 번째 element를 리턴 하는것이 정상이라 문제 없어야 하지만

카탈론 내부적 문제인지 `//td[1]/select` 정확하게 잡아야 정상 작동하는 듯 하다.

단순한 일시적 문제 일 수도 있다..

위 방법을 맹신하지 말고 label에 불필요한 white space가 포함되어 있는지도 확인해 볼 필요가 있다. = =)