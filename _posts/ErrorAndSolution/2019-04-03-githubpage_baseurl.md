---
layout: post
current: post
title:  "GitPage - Baseurl"
navigation: True
tags: [ErrorAndSolution]
class: post-template
subtitle: "호스팅 할 때 baseurl 문제"
background: assets/images/cover/github-pages.png
cover: assets/images/cover/github-pages.png
subclass: 'post tag-getting-started'
author: mem
---


Baseurl
=======

## 문제 상황

1. 지킬 실행 시 local에서는 정상적으로 작동하는데, github page에서 css가 깨지는 현상
2. netlify로 호스팅할 때 build fail로 deploy 안되는 현상

## 원인

1. **baseurl**, url 설정
2. destination folder

## 해결

1. 현재 github page로 호스팅할 때 'baseurl: /' 로 설정하면 'baseurl: ' 로 인식한다고 한다 =.= [1][1]
일시적인 해결방안이지만 `baseurl: `로 설정하고 `{{site.baseurl}}` 을 `/{{site.baseurl}}` 로 바꾸면 된다고함.

그러나 호스팅을 github page로 하지 않고 다른 서비스로 배포하면 정상작동한다.(나는 netlify를 사용함)

2. netlify의 경우 publish directory와 _config.yml 내의 destination과 같게 해주어야함

## baseurl

github page를 만들 때 주소는
`username.github.io` 이런식으로 될것임. 이것을 root domain 이라고 하고, 이 뒤에 baseurl이 붙게된다.
baseurl을 사용하는 이유는 테스트하는 내부 웹서버의 url과 배포 서버의 url을 같게하기 위해서라고함.[2][2]

해당 사이트 도메인의 기본 경로라고 생각하면 된다. [3][3] 예를들어 baseurl을 home으로 한다면, 이 사이트의 주소는 `https://localhost:4000/home/` 이 될 것임 `https://localhost:4000/`로 들어가면 아무것도 볼 수 없다.

## url

내가 deploy 하려고하는 주소를 전체를 입력해야함. 홈 주소를 써주면됨. 이거 설정 안하면 오류난다.

***

## Addition : netlify

github page로 배포할 때 repository 이름에 신경써야하고 여러 개의 사이트를 만들고싶으면 서브도메인으로 만들고 커스텀 도메인을 만드려면 CNAME 설정을 해주는 등등. 신경써야할게 제법 있어서 초보 입장에서는 한 번 꼬이면 어디가 문제인지 찾는것도 시간이 걸렸다.[4][4]

netlify는 repository의 이름과 상관없이 github repository와 연동해서 새로운 코드가 push 될 때 마다 자동으로 deploy해준다. netlify app 홈페이지에서 커스텀 도메인 설정이 가능하다. CDN 통해 배포한다는데 속도도 괜찮았음. 장점이랑 튜토리얼은 [이 블로그](https://blog.outsider.ne.kr/1417) 에서 설명을 잘 해주셨다.

다만 이 블로그는 react 파일을 배포할 때의 예제이고, 지킬을 사용할거라면 build command는 `bundle exec jekyll build` 로 publish directory는 _config.yml의 **destination folder 명**과 같게 해줘야한다.

[1]: https://github.com/jekyll/jekyll/pull/235
[2]: https://kairos03.github.io/jekyll/2017/09/11/learing-Up-Confusion-Around-baseurl.html#fn:1
[3]: http://blog.saltfactory.net/setting-domain-name-in-github-pages-via-cname/
[4]: https://github.com/github/pages-gem/issues/350#issuecomment-317234161



