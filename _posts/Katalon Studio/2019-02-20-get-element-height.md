---
layout: post
title:  "Web UI element 2"
subtitle: "get page width, get url, get viewport height, get viewport left position, get viewport top position, get viewport width"
background: '/img/posts/katalonlogo.png'
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

* ## Example

```groovy

'Mouse over on \'Book Appointment\' button'
WebUI.mouseOver(findTestObject('Page_CuraAppointment/btn_BookAppointment'), 'font-size')

```

---

# 3. Right Click/Click Offset

* ## Description

* ## Parameter

* ## Returns

* ## Example

---

# 4. Scroll To Element

* ## Description

* ## Parameter

* ## Returns

* ## Example

---