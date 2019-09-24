---
layout: post
cover: assets/images/cover/pythonlogo.png 
title:  "파이썬 기초"
navigation: True
tags: [Python]
class: post-template
subtitle: "dir(), list"
background: assets/images/cover/pythonlogo.png 
subclass: 'post tag-getting-started'
author: mem
---


# dir

클래스 안에 어떤 메소드가 있는지 확인 할 수 있다.
`dir(str)`

# list

a = [1,2,3,4,5,6]

a[0]
1
a][-1]
6

리스트를 슬라이싱하면 리스트가 리턴된다
a[0:1]
[1]
a[0:2]
[1,2]

a=[1,2,3,4,[123,1231]]
a[-1]
[123,1231]
a[-1:]
[[123,1231]]

# 내장 함수

abs()
sum()
all()
any()
chr() 유니코드에 해당하는 문자를 리턴
ord() 문자를 주면 코드 값을 줌
oct()
hex()
isinstance(a,int)
round(a,3) 반올림 세번째 자리

