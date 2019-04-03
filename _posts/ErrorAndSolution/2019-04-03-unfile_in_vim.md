---
layout: post
current: post
title:  "Vim - un 파일"
navigation: True
tags: [ErrorAndSolution]
class: post-template
subtitle: ".un file 자동생성 끄기"
background: assets/images/jekyll.png
subclass: 'post tag-getting-started'
author: mem
---

## Problem
vim 실행 후 저장시 .un파일이 생성됨. undo 기능을 위해 자동으로 생성되는 파일인데 자동생성을 끄기 위해서 다음과 같이 해주면 된다.

> vim 파일이름 set noundofile

> vimrc 에서 설정을 입력해주면 더 좋다. (set noundofile 추가)
