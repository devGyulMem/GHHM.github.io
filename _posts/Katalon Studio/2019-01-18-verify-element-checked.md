---
layout: post
current: post
cover: assets/images/cover/katalonlogo.png 
title:  "Verify Element Checked"
navigation: True
tags: [Katalon Studio]
class: post-template
subtitle: "Verify element checked, deselect all option, deselect option by index, deselect option by value, get number of selected option, get number of total option"
background: assets/images/cover/katalonlogo.png 
subclass: 'post tag-getting-started'
author: mem
---

***

Katalon Studio
===

김혜미
---

***

# Index
 1. Verify Element Checked
 2. Deselect All Option
 3. Deselect Option By Index
 4. Deselect Option By Value
 5. Get Number Of Selected Option
 6. Get Number Of Total Option
 7. 문서 Assertions, Keyword 메뉴 확인    Assert를 사용해서 성공/실패 예제 만들기

***

1 Verify Element Checked
----------

* ## Description
지정된 체크박스 web element가 체크되었는지 확인한다.

***

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to | TestObject | Required  | web element를 나타낸다.       |
| timeout | int | Requried  | 시스템은 결과를 리턴하기 위해 타임아웃(초단위)때 까지 기다린다.   |
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |

***

* ## Returns

| Param Types | Description |
|:-----------:|:-----------:|
| boolean     | verification 결과 |
| |  (true: element checked, false: element unchecked)|

***

* ## Example

```groovy
'Open browser and navigate to demo AUT site'
WebUI.openBrowser('http://demoaut.katalon.com/')

'Click on \'Make Appointment\' button'
WebUI.click(findTestObject('Page_CuraAppointment/btn_BookAppointment'))

WebUI.verifyElementChecked(findTestObject('Page_CuraAppointment/chk_Medicaid'), 10)

'Close Browser'
WebUI.closeBrowser()
```

***

* ## Example 2

```groovy

WebUI.openBrowser("https://www.w3schools.com/tags/tryit.asp?filename=tryhtml5_input_type_checkbox")

isChecked = WebUI.verifyElementChecked(findTestObject('Object Repository/Checkbox/Page_Tryit Editor v3.6/input_I have a boat'), 5)

println(isChecked)

```

***

2 Deselect All Option
----------

* ## Description
콤보박스에서 모든 옵션을 선택 해제한다.

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to | TestObject | Required  | web element를 나타낸다.       |
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다. |

***

* ## Example

```groovy
'Open browser and navigate to demo AUT site'
WebUI.openBrowser('http://demoaut.katalon.com/')

'Click on \'Make Appointment\' button'
WebUI.click(findTestObject('Page_CuraAppointment/btn_BookAppointment'))

'Deselect all options on \'Facility\' list'
WebUI.deselectAllOption(findTestObject('Page_CuraAppointment/lst_Facility'))

'Close Browser'
WebUI.closeBrowser()
```

***

3 Deselect Option By Index
--------

* ## Description
콤보박스에서 주어진 인덱스의 옵션을 선택 해제 한다. 인덱스는 0부터 시작한다.

***

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to | TestObject | Required  | web element를 나타낸다.       |
| range | Object | Reqruied | 선택해제할 인덱스 범위 |
| | | |  2 - 인덱스2 , "2,3" - 인덱스 2와 3, "2-5" - 인덱스 2에서 5까지 즉 2,3,4,5 |
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.|

***

* ## Example

```groovy
'Open browser and navigate to demo AUT site'
WebUI.openBrowser('http://demoaut.katalon.com/')

'Click on \'Make Appointment\' button'
WebUI.click(findTestObject('Page_CuraAppointment/btn_BookAppointment'))

'Deselect option 1 on \'Facility\' list'
WebUI.deselectOptionByIndex(findTestObject('Page_CuraAppointment/lst_Facility'), 1)

'Close Browser'
WebUI.closeBrowser()
```

***

4 Deselect Option By Label
------

* ## Description
콤보박스에서 지정된 레이블(보여지는 텍스트)를 사용하여 옵션을 선택 해제한다.

***

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| to | TestObject | Required  | web element를 나타낸다.       |
| labelText | String | Required | 선택해제할 옵션의 표시된 텍스트 |
| isRegex | boolean | Required | true: 레이블 값이 일반적인 표현식일때, false: true 외의 모든 상황 |
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |

***

* ## Example

```groovy
'Open browser and navigate to demo AUT site'
WebUI.openBrowser('http://demoaut.katalon.com/')

'Click on \'Make Appointment\' button'
WebUI.click(findTestObject('Page_CuraAppointment/btn_BookAppointment'))

'Select \"Hongkong CURA Healthcare Center\" option'
WebUI.selectOptionByValue(findTestObject('Page_CuraAppointment/lst_Facility'), 'Hongkong CURA Healthcare Center', false)

'Deselect \"Hongkong CURA Healthcare Center\" option'
WebUI.deselectOptionByLabel(findTestObject('Page_CuraAppointment/lst_Facility'), 'Hongkong CURA Healthcare Center', false)

'Close Browser'
WebUI.closeBrowser()
```

***

5 Get Number Of Selected Option
------

* ## Description
주어진 콤보박스 web element 에서 선택된 옵션의 수를 센다.

***

* ## Parameter

| Param | Param Type | Mandatory | Description |
|:-----:|:----------:|:---------:|:-----------:|
| to | Testobject | Required | Represent a web element |
| flowControl | FailureHandling | Optional | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다. |

***

* ## Returns

| Param Type | Description |
|:----------:|:------------:|
| int | 선택된 옵션의 수 |

***

* ## Example

```groovy
'Open browser and navigate to demo AUT site'
WebUI.openBrowser('http://demoaut.katalon.com/')

'Click on \'Make Appointment\' button'
WebUI.click(findTestObject('Page_CuraAppointment/btn_BookAppointment'))

'Select \"Hongkong CURA Healthcare Center\" option'
WebUI.selectOptionByValue(findTestObject('Page_CuraAppointment/lst_Facility'), 'Hongkong CURA Healthcare Center', false)

'Get number of selected option in Facility list'
WebUI.getNumberOfSelectedOption(findTestObject('Page_CuraAppointment/lst_Facility'))

'Close Browser'
WebUI.closeBrowser()

```

***

6  Get Number Of Total Option
------

* ## Description
주어진 콤보박스 web element가 가진 옵션의 총 수를 센다.

***

* ## Parameter

| Param | Param Type | Mandatory | Description |
|:-----:|:----------:|:---------:|:-----------:|
| to | Testobject | Required | Represent a web element |
| flowControl | FailureHandling | Optional | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다. |

* ## Returns
| Param Type | Description |
|:----------:|:------------:|
| int | 총 옵션의 수 |

***

* ## Example

```groovy
'Open browser and navigate to demo AUT site'
WebUI.openBrowser('http://demoaut.katalon.com/')

'Click on \'Make Appointment\' button'
WebUI.click(findTestObject('Page_CuraAppointment/btn_BookAppointment'))

'Get number of total option in Facility list'
WebUI.getNumberOfTotalOption(findTestObject('Page_AppointmentConfirmation/lbl_Facility'))

'Close Browser'
WebUI.closeBrowser()
```