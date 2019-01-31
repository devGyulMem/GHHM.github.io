---
layout: post
title:  "Assertions"
subtitle: ""
background: '/img/posts/katalonlogo.png'
---

* ## Example 

```groovy

sum = 0

def assertions = {
	for(int i=0;i<10;i++){
		sum = sum + i
		println(sum)
	}
}

assert sum == 0

assertions()

assert sum == 45


```


* ## Example 2

```groovy

WebUI.openBrowser("https://www.w3schools.com/tags/tryit.asp?filename=tryhtml5_input_type_checkbox")

//isChecked = WebUI.verifyElementChecked(findTestObject('Object Repository/Checkbox/Page_Tryit Editor v3.6/input_I have a boat'), 5)

//WebUI.check(findTestObject('Object Repository/Checkbox/Page_Tryit Editor v3.6/input_I have a bike'))

isChecked = WebUI.verifyElementChecked(findTestObject('Object Repository/Checkbox/Page_Tryit Editor v3.6/input_I have a boat'),5)

isNotChecked = WebUI.verifyElementNotChecked(findTestObject('Object Repository/Checkbox/Page_Tryit Editor v3.6/input_I have a bike'),5)

assert isChecked == true
assert isNotChecked == true

```