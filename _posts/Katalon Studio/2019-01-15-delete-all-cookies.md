---
layout: post
title:  "WebUI Keywords"
subtitle: "Delete all cookies, Execute JavaScript, Forward, Get Page Height"
background: '/img/posts/01.jpg'
---


1.Delete All Cookies
--------
[Delete All Cookies][1]

모든 윈도우의 모든 쿠키를 삭제할 때 사용한다

* 
### Parameter

| Param       | Param Type      | Mandatory | Description                                                                                              |
|:-----------:|:---------------:|:---------:|:--------------------------------------------------------------------------------------------------------:|
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.                                   |

<br>

* 
### 핵심 코드
`WebUI.deleteAllCookies()`

* 
### Example
브라우저의 모든 창을 닫고 싶을 때

```java
import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
import com.kms.katalon.core.checkpoint.CheckpointFactory as CheckpointFactory
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as MobileBuiltInKeywords
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import com.kms.katalon.core.model.FailureHandling as FailureHandling
import com.kms.katalon.core.testcase.TestCase as TestCase
import com.kms.katalon.core.testcase.TestCaseFactory as TestCaseFactory
import com.kms.katalon.core.testdata.TestData as TestData
import com.kms.katalon.core.testdata.TestDataFactory as TestDataFactory
import com.kms.katalon.core.testobject.ObjectRepository as ObjectRepository
import com.kms.katalon.core.testobject.TestObject as TestObject
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WSBuiltInKeywords
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUiBuiltInKeywords
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
import internal.GlobalVariable as GlobalVariable
import org.openqa.selenium.Keys as Keys

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

<br>

2.Execute JavaScript
---

[Execute JavaScript][2]

현재 선택된 프레임 혹은 윈도우에서 자바스크립트를 실행한다. 제공된 스크립트 프레그먼트는 익명 함수의 바디로써 실행된다.

* 
### Parameter

| Param       | Param Type      | Mandatory | Description |
|:-----------:|:---------------:|:---------:|:-----------:|
| script      | String | Required | 실행할 자바스크립트    |
| argument    | List | Required | 스크립트의 argument. 비워두거나 null 가능 |
| flowControl | FailureHandling | Optional | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다. |

* 
### Return
Boolean, Long, Double, String, List, WebElement, or Null

* 
### 핵심 코드
`WebUI.executeJavaScript()`

* 
### Example
* 웹페이지에 alert 띄우기 <br>
`WebUI.executeJavaScript( "alert('This is an alert')" , null)`

* id 기반의 WebElement 리턴받기 <br>
`WebElement element = WebUI.executeJavaScript("return document.getElementById('someId');", null)`

* 리턴된 WebElement와 상호작용 <br>
`WebElement element = WebUiCommonHelper.findWebElement(findTestObject('your/object'),30)
WebUI.executeJavaScript("arguments[0].style.border='3px solid blue'", Arrays.asList(element))`

* 리턴된 WebElement 클릭하기 <br>
`WebElement element = WebUiCommonHelper.findWebElement(findTestObject('your/object'),30)
WebUI.executeJavaScript("arguments[0].click()", Arrays.asList(element))`


***

<br>

3.Forward
---

사용자가 브라우저의 '앞으로' 버튼 누르는 것을 시뮬레이션

[Forward][3]

현재 선택된 프레임 혹은 윈도우에서 자바스크립트를 실행한다. 제공된 스크립트 프레그먼트는 익명 함수의 바디로써 실행된다.

* 
### Parameter

| Param       | Param Type      | Mandatory | Description |
|:-----------:|:---------------:|:---------:|:-----------:|
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다. |

* 
### 핵심 코드
`WebUI.forward()`

* 
### Example

```java
import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
import com.kms.katalon.core.checkpoint.CheckpointFactory as CheckpointFactory
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as MobileBuiltInKeywords
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import com.kms.katalon.core.model.FailureHandling as FailureHandling
import com.kms.katalon.core.testcase.TestCase as TestCase
import com.kms.katalon.core.testcase.TestCaseFactory as TestCaseFactory
import com.kms.katalon.core.testdata.TestData as TestData
import com.kms.katalon.core.testdata.TestDataFactory as TestDataFactory
import com.kms.katalon.core.testobject.ObjectRepository as ObjectRepository
import com.kms.katalon.core.testobject.TestObject as TestObject
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WSBuiltInKeywords
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUiBuiltInKeywords
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
import internal.GlobalVariable as GlobalVariable
import org.openqa.selenium.Keys as Keys

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

<br>

4.Get Page Height
---

[Get Page Height][4]

* 
### Parameter

| Param       | Param Type      | Mandatory | Description |
|:-----------:|:---------------:|:---------:|:-----------:|
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다. |

* 
### Returns

| Param Type | Description |
|:----------:|:-----------:|
| int | 현재 웹 페이지의 높이(height) |

* 
### 핵심 코드

`height = WebUI.getPageHeight()`

* 
### Example

현재 웹 브라우저의 페이지 높이를 알고싶다. 아웃풋은 변수 "height"에 저장.

```java
import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
import com.kms.katalon.core.checkpoint.CheckpointFactory as CheckpointFactory
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as MobileBuiltInKeywords
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import com.kms.katalon.core.model.FailureHandling as FailureHandling
import com.kms.katalon.core.testcase.TestCase as TestCase
import com.kms.katalon.core.testcase.TestCaseFactory as TestCaseFactory
import com.kms.katalon.core.testdata.TestData as TestData
import com.kms.katalon.core.testdata.TestDataFactory as TestDataFactory
import com.kms.katalon.core.testobject.ObjectRepository as ObjectRepository
import com.kms.katalon.core.testobject.TestObject as TestObject
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WSBuiltInKeywords
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUiBuiltInKeywords
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
import internal.GlobalVariable as GlobalVariable

'Open browser and navigate to website katalon.com'
WebUI.openBrowser('https://www.katalon.com/')

'Get current page\'s height'
height = WebUI.getPageHeight()

'Close browser'
```

[1]: https://docs.katalon.com/katalon-studio/docs/webui-delete-all-cookies.html
[2]: https://docs.katalon.com/katalon-studio/docs/webui-execute-javascript.html
[3]: https://docs.katalon.com/katalon-studio/docs/webui-forward.html
[4]: https://docs.katalon.com/katalon-studio/docs/webui-get-page-height.html