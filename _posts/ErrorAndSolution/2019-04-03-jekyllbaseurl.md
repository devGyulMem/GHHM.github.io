---
layout: post
current: post
title:  "Jekyll - Baseurl"
navigation: True
tags: [ErrorAndSolution]
class: post-template
subtitle: "지킬 실행 시 local에서 정상작동하나 github page에서 css가 깨지는 문제"
background: assets/images/cover/jekyll.png
subclass: 'post tag-getting-started'
author: mem
---

============
Jekyll
============

##Error
Jekyll theme를 하나 받아서 돌렸음. 로컬에서는 잘 동작하는데 호스팅하는 순간 css가 안먹는다..
 config.yml 에서 base-url을 잘못 설정해서 그렇다.

##Solution
### baseurl
root 주소를 넣어준다. git 에서 clone 했다면 프로젝트 명.
> baseurl:         "GHHM.githu.io"

gitpage를 사용안하고 다른 방식으로 호스팅 할 때
> baseurl:           "/"

### url
도메일 주소가 바뀌면 바꿔줘야한다.
github page로 호스팅할 경우 => url: "https://ghhm.github.io/"
이외의 사이트를 사용할 경우 (아래 예시는 netlify를 사용)
> url:               "https://memlearning.netlify.com/

*참고
bundle exec 로 돌리면 무조건 로컬(124.0.0.1)에서 돌아간다.
> bundle exec jekyll serve

> bundle exec jekyll build
