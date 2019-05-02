---
layout: post
current: post
title:  "Web driver 실행 에러 발생"
navigation: True
tags: [ErrorAndSolution, KatalonStudio]
class: post-template
subtitle: "Chromedriver 버전 문제"
background: assets/images/git.png
cover: assets/images/git.png
subclass: 'post tag-getting-started'
author: mem
---


# Problem

코드상 아무런 문제 없는데 아래와 같이 뜨면서 실행이 안됨

`
Reason:
com.kms.katalon.core.exception.StepFailedException: Unable to open browser with url: '' (Root cause: com.kms.katalon.core.exception.StepFailedException: Unable to open browser with url: ''
	at com.kms.katalon.core.webui.keyword.internal.WebUIKeywordMain.stepFailed(WebUIKeywordMain.groovy:64)
	at com.kms.katalon.core.webui.keyword.internal.WebUIKeywordMain.runKeyword(WebUIKeywordMain.groovy:26)
`

# Reason 

**크롬 드라이버와 크롬의 버전 때문에 생기는 문제**였다. (만일 다른 웹 드라이버를 사용하고 있다해도 마찬가지.. 버전을 맞춰줘야한다.)

[크롬 드라이버 다운로드 페이지](http://chromedriver.chromium.org/downloads) 에 가서 보면 ..

> If you are using Chrome version 75, please download ChromeDriver 75.0.3770.8 <br>
> If you are using Chrome version 74, please download ChromeDriver 74.0.3729.6 <br>
> If you are using Chrome version 73, please download ChromeDriver 73.0.3683.68 <br>

이렇게 아주 친절하게 써놓았다...

당연한 말이지만 내 크롬 버전에 맞는 크롬 드라이버를 써야 정상작동한다.

Katalon Studio의 경로를 따라 가서 chromedriver의 버전을 확인해보면 

* Katalon Studio에서 chromedriver 버전 확인 방법
> 카탈론에서 크롬 드라이버 위치는 `KatalonStudio폴더\configuration\resources\drivers\` 이다. <br> 
> cmd 창에서 해당 위치로 이동해 다음과 같이 입력 <br>
> `chromedriver.exe -v` <br><br>
> 결과 <br>
> `ChromeDriver 73.0.3683.68 (47787ec04b6e38e22703e856e101e840b65afe72)`

73 버전이기 때문에 74버전의 크롬 에서는 작동이 안되는 것이였다.

카탈론 스튜디오를 다운받으면 자동으로 73 버전이 받아지기 때문에 내 크롬 버전과 다르다면 교체해줘야한다.

웹 드라이버 및 셀레니윰의 업데이트 방법은 [여기](https://docs.katalon.com/katalon-studio/docs/update-or-replace-web-browser-drivers-and-selenium.html#how-to-replace)
에서 확인 가능하다.

# Solution

내 웹 페이지 버전과 웹 드라이버의 버전을 맞춰준다.

크롬 업데이트 할 때는 조심=_= 갑자기 안돼서 코드 문제인줄 알고 열심히 work tree 돌아다녔음..

해결하고보면 쉬운데.. 초보라서 그런지 까다로웠음 ㅠ

# Addition
어떤 사람은 비슷한 문제를 접했는데 이렇게 해결했다고함. -> [chrome driver 에러 발생시 해결방법](https://league-cat.tistory.com/278)

에러메시지는 비슷한거 같은데.. 원인이 달랐던거같음.

```
chrome_options = webdriver.ChromeOptions()
chrome_options.add_argument('--headless')
chrome_options.add_argument('--no-sandbox')
chrome_options.add_argument('--disable-dev-shm-usage')

driver = webdriver.Chrome(executable_path="/home/streamsets/crawlingExe/chromedriver",chrome_options=chrome_options)
```



버전 문제 때문에 삽질 오지게햇네....


