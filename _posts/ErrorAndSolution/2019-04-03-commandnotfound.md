---
layout: post
current: post
title:  "[MacOS] Mac terminal 에서 Command not found"
navigation: True
tags: [ErrorAndSolution]
class: post-template
subtitle: "path 설정 오류"
subclass: 'post tag-getting-started'
author: mem
---

## Error
command not found on mac terminal

## Solution
Find '.bash_profile' file in home directory
and check

~/.bash_profile 혹은 ~/.profile을 찾음
다음을 추가

> export PATH=%PATH:/bin:/usr/local/bin:/usr/bin

or

> export PATH=/usr/bin:/usr/sbin:/bin:/usr/local/bin:/sbin:/opt/x11/bin:$PATH

* /sbin 없으면
ifconfig 안됨
 
* 명령어가 먹히지 않아서 위 파일을 열수 없을 경우
  - 맥 숨긴파일 보기: http://sevensign.tistory.com/333

(if you can not use 'vi' command, fine it via finder)

## Reference
* https://medium.com/@devfallingstar/macos-터미널에서-command-not-found가-계속-뜰-때-138d7fe6a3fe

