---
layout: post
current: post
cover: assets/images/katalonlogo.png 
title:  "WebUI Element 3"
navigation: True
tags: [Katalon Studio]
class: post-template
subtitle: "get element height/left position/width, mouse over/over offset, right click/click offset, scroll to element"
background: assets/images/katalonlogo.png 
subclass: 'post tag-getting-started'
author: mem
---

# Index
## Get Element Height
## Get Element Left Position
## Get Element Width
## Mouse Over
## Mouse Over Offset
## Right Click
## Right Click Offset
## Scroll To Element

---

# 1. Get Element Height/Left Position/Width

* ## Description
Web element의 높이/좌측 좌표/넓이 를 가져온다.

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to          | TestObject      | Required  | 구하려는 web element      |
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |


* ## Returns

| Param Types | Description |
|:-----------:|:-----------:|
| int     | height |

* ## Example

```groovy
'Open browser and navigate to AUT'
WebUI.openBrowser(GlobalVariable.G_SiteURL)
 
'Get height of txt_UserName'
height = WebUI.getElementHeight(findTestObject('Page_Login/txt_UserName'))

'Get left position of txt_UserName'
leftPosition = WebUI.getElementLeftPosition(findTestObject('Page_Login/txt_UserName'))
 
'Get width of txt_UserName'
width = WebUI.getElementWidth(findTestObject('Page_Login/txt_UserName'))

'Close browser'
WebUI.closeBrowser()
```

---

# 2. Mouse Over/Over Offset

* ## Description
주어진 element에 마우스를 올려놓는 동작을 함

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to          | TestObject      | Required  | 구하려는 web element      |
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to          | TestObject      | Required  | 구하려는 web element      |
| offsetX     | int       | Required | element의 상대적인 x 위치 |
| offsetY     | int       | Required | element의 상대적인 y 위치 | 
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |

* ## Example

```groovy

'Mouse over on \'Book Appointment\' button'
WebUI.mouseOver(findTestObject('Page_CuraAppointment/btn_BookAppointment'))

WebUI.mouseOverOffset(findTestObject('Page_Bar Chart/canvas_chart'), 20, 30)

```

---

# 3. Right Click/Click Offset

* ## Description
주어진 element를 우클릭한다.

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to          | TestObject      | Required  | 구하려는 web element      |
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to          | TestObject      | Required  | 구하려는 web element      |
| offsetX     | int       | Required | element의 상대적인 x 위치 |
| offsetY     | int       | Required | element의 상대적인 y 위치 | 
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |

* ## Example

```groovy

'Right click on \'Book Appointment\' button'
WebUI.rightClick(findTestObject('Page_CuraHomepage/btn_MakeAppointment'))

'Right-click on the top left cell'
WebUI.rightClickOffset(findTestObject('Object Repository/Page_CodePen - Tic Tac Toe/canvas_tic-tac-toe-board'), 100, 100)

```

---

# 4. Scroll To Element

* ## Description

element가 보이는 위치로 브라우저 윈도우를 스크롤한다.

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to          | TestObject      | Required  | 구하려는 web element      |
| timeout | int | Required | 
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |

* ## Example

```groovy

'Scroll to \'Book Appointment\' button'
WebUI.scrollToElement(findTestObject('Page_CuraHomepage/btn_MakeAppointment'), 3)

```

---