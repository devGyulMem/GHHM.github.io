---
layout: post
current: post
cover: assets/images/cover/katalonlogo.png 
title:  "WebUI Element 1"
navigation: True
tags: [Katalon Studio]
class: post-template
subtitle: "Delete all cookies, Execute JavaScript, Forward, Get Page Height"
background: assets/images/cover/katalonlogo.png 
subclass: 'post tag-getting-started'
author: mem
---

Katalon Studio
===

### 김혜미

***

# Index
## - deleteAllCookies
## - executeJavaScript
## - Forward
## - getPageHeight


***

1 [deleteAllCookies][1]
--------


모든 윈도우의 모든 쿠키를 삭제할 때 사용한다

* ### Parameter

| Param       | Param Type      | Mandatory | Description                                                                                              |
|:-----------:|:---------------:|:---------:|:--------------------------------------------------------------------------------------------------------:|
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.                                   |


* ### 핵심 코드
`WebUI.deleteAllCookies()`

***

* ### Example
브라우저의 모든 창을 닫고 싶을 때

```java
'Open browser and navigate to demo AUT site'
WebUI.openBrowser('')

'Delete all cookies after browser is opened'
WebUI.deleteAllCookies()

'Navigate to demo AUT site'
WebUI.navigateToUrl('http://demoaut.katalon.com/')

'Close browser'
WebUI.closeBrowser()
```

***

2 [executeJavaScript][2]
---

현재 선택된 프레임 혹은 윈도우에서 자바스크립트를 실행한다. 제공된 스크립트 프레그먼트는 익명 함수의 바디로써 실행된다.

* ### Return
Boolean, Long, Double, String, List, WebElement, or Null

* ### 핵심 코드
`WebUI.executeJavaScript()`

***

* ### Parameter

| Param       | Param Type      | Mandatory | Description |
|:-----------:|:---------------:|:---------:|:-----------:|
| script      | String | Required | 실행할 자바스크립트    |
| argument    | List | Required | 스크립트의 argument. 스크립트를 실행하기 위해 필요한 값. 비워두거나 null 가능 |
| flowControl | FailureHandling | Optional | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다. |

***

* ### Example 1
* * 웹페이지에 alert 띄우기
`WebUI.executeJavaScript( "alert('This is an alert')" , null)`

* * id 기반의 WebElement 리턴받기 
`WebElement element = WebUI.executeJavaScript("return document.getElementById('someId');", null)`

***

* ### Example 2

* * 리턴된 WebElement와 상호작용 
`WebElement element = WebUiCommonHelper.findWebElement(findTestObject('your/object'),30)
WebUI.executeJavaScript("arguments[0].style.border='3px solid blue'", Arrays.asList(element))`

* * 리턴된 WebElement 클릭하기 
`WebElement element = WebUiCommonHelper.findWebElement(findTestObject('your/object'),30)
WebUI.executeJavaScript("arguments[0].click()", Arrays.asList(element))`


***


3 [Forward][3]
---

사용자가 브라우저의 '앞으로' 버튼 누르는 것을 시뮬레이션

* ### Parameter

| Param       | Param Type      | Mandatory | Description |
|:-----------:|:---------------:|:---------:|:-----------:|
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다. |


* ### 핵심 코드
`WebUI.forward()`

***

* ### Example

```java

'Open browser'
WebUI.openBrowser('')

'Navigate to demo AUT site'
WebUI.navigateToUrl('http://demoaut.katalon.com/')

'Click on \'Make Appointment\' button'
WebUI.click(findTestObject('Page_CuraHomepage/btn_MakeAppointment'))

'Back to homepage'
WebUI.back()

'Forward to \'Make Appointment\' page'
WebUI.forward()

'Close browser'
WebUI.closeBrowser()
```


***

4 [Get Page Height][4]
---

* ### Parameter

| Param       | Param Type      | Mandatory | Description |
|:-----------:|:---------------:|:---------:|:-----------:|
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다. |

* ### Return

| Param Type | Description |
|:----------:|:-----------:|
| int | 현재 웹 페이지의 높이(height) |

* ### 핵심 코드

`height = WebUI.getPageHeight()`

***

* ### Example

현재 웹 브라우저의 페이지 높이를 알고싶다. 아웃풋은 변수 "height"에 저장.

```java
'Open browser and navigate to website katalon.com'
WebUI.openBrowser('https://www.katalon.com/')

'Get current page\'s height'
height = WebUI.getPageHeight()

'Close browser'
```


***

### 적용

* 'btn-login' 라는 id를 가진 WebElement를 가져와서 클릭한다.

```java
import org.openqa.selenium.WebElement

import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI

import internal.GlobalVariable as GlobalVariable

WebUI.openBrowser(GlobalVariable.G_url_loginPage)

WebElement element = WebUI.executeJavaScript("return document.getElementById('btn-login');",null)

element.click()
```

***

* WebElement의 정보를 가져와서 alert로 띄우기

```java
//로그인 페이지 열기
WebUI.openBrowser(GlobalVariable.G_url_loginPage)

//자바스크립트를 실행하여 id와 pw element를 가져와 입력한 후 클릭한다.
WebElement input_id = WebUI.executeJavaScript("return document.getElementById('id')", null)
WebElement input_pw = WebUI.executejavaScript("return document.getElementById('pw')", null)

// input_id 의 box size와 page size를 가져와서 alert로 송출
if(input_id != null)
size = input_id.getSize()

height = WebUI.getPageHeight()

String result = "The size of id box is " + size + "and page height is "+height
String message = "alert("+"'"+result+"');"

WebUI.executeJavaScript(message, null)
```

***

* id로 가져온 WebElement로 로그인 하기

```java
//로그인 페이지 열기
WebUI.openBrowser(GlobalVariable.G_url_loginPage)

//자바스크립트를 실행하여 id와 pw element를 가져와 입력한 후 클릭한다.
WebElement input_id = WebUI.executeJavaScript("return document.getElementById('id');", null)
WebElement input_pw = WebUI.executeJavaScript("return document.getElementById('password');", null)
WebElement btn_login = WebUI.executeJavaScript("return document.getElementById('btn-login');", null)

//TestObject로 가져왔을 경우 setText를 사용하였지만, 지금은 WebElement이기 때문에 sendKeys를 사용
if(input_id != null)
input_id.sendKeys('khmmanager')

if(input_pw != null)
input_pw.sendKeys('13301330!@')

if(btn_login != null)
btn_login.click()

//WebElement element = WebUiCommonHelper.findWebElement((TestObject)findTestObject('Object Repository/loginPage/Page_/button_login'),30)
//WebUI.executeJavaScript("arguments[0].click()", Arrays.asList(element))

```

***

* 로그인 후 뒤로가기

``` java
WebUI.openBrowser(GlobalVariable.G_url_loginPage)

WebElement element = WebUiCommonHelper.findWebElement((TestObject)findTestObject('Object Repository/loginPage/Page_/button_login'),30)


WebUI.setText(findTestObject('Object Repository/loginPage/Page_/input__id'), 'khmmanager')
WebUI.setText(findTestObject('Object Repository/loginPage/Page_/input__password'), '13301330!@')

WebUI.executeJavaScript("arguments[0].style.border='10px solid blue'", Arrays.asList(element))

WebUI.executeJavaScript("arguments[0].click()", Arrays.asList(element))

//뒤로: back() 앞으로: forward()
WebUI.back()
WebUI.forward()
```

***

* 자동 import 단축키 : ctrl+shift+o

[1]: https://docs.katalon.com/katalon-studio/docs/webui-delete-all-cookies.html
[2]: https://docs.katalon.com/katalon-studio/docs/webui-execute-javascript.html
[3]: https://docs.katalon.com/katalon-studio/docs/webui-forward.html
[4]: https://docs.katalon.com/katalon-studio/docs/webui-get-page-height.html