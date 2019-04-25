---
layout: post
cover: assets/images/katalonlogo.png 
title:  "Dynamic test object"
navigation: True
tags: [Katalon Studio]
class: post-template
subtitle: "정적 및 동적 테스트 오브젝트 핸들링"
background: assets/images/katalonlogo.png 
subclass: 'post tag-getting-started'
author: mem
---

# Introduction
static test object와 dynamic test object의 접근 차이에 대해 설명하겠다.

# Requirement
* 기본적인 Java/Groovy 문법
* Katalon studio에서 script view로 작성할 수 있어야한다.

# Static object
변하지 않아 다루기 쉽다.
Object Repository에 가서 새 오브젝트를 만들고, 선호하는 셀렉터를 고른다. element를 저장하고 built-in 메소드(findTestElement(String pathInRepository))로 테스트 오브젝트를 가져온다.

# Dynamic object

## 1. testcase에 직접 test object 선언하기

```groovy
import com.kms.katalon.core.testobject.ConditionType
import com.kms.katalon.core.testobject.TestObject
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
String dynamicId = ‘Katalon123’
String xpath = ‘//div[@id=”’ + dynamicId + ‘“]’
TestObject to = new TestObject(“objectName”)
to.addProperty(“xpath”, ConditionType.EQUALS, xpath)
WebUI.click(to)
```

[ConditionType API 설명서](https://api-docs.katalon.com/com/kms/katalon/core/testobject/ConditionType.html)

이렇게 쓰면 단점은.. 여러 테스트 케이스에서 동일한 객체를 사용해야할 때 유지 관리가 쉽지 않다.


## 2. 동적 셀렉터를 위한 별도의 키워드 만들기

여러 페이지의 여러 개의 키워드를 테스트 프로젝트에 포함시키기 용이하다.

* 셀렉터

 String.format() 메소드의 %s 와일드 카드를 사용.

```groovy
package mypackage
 
public class MySelectors {
public static final String dynamicIdPath = '//div[@id="%s"]'
 
}
```

* 테스트 케이스

```groovy
import com.kms.katalon.core.testobject.ConditionType
import com.kms.katalon.core.testobject.TestObject
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
 
import mypackage.MySelectors
 
String dynamicId = 'Katalon123'
String xpath = String.format(MySelectors.dynamicIdPath, dynamicId)
TestObject to = new TestObject("objectName")
to.addProperty("xpath", ConditionType.EQUALS, xpath)
WebUI.click(to)
```

* 혹은 셀릭터 값 자체를 대체하는 방법도 있다.

```groovy
public static final String dynamicIdPath = '//div[@id="<<dynamicId>>"]'
// a line in test case:
String xpath = MySelectors.dynamicIdPath.replace("<<dynamicId>>", dynamicId)
```


## 3. 동적 테스트 객체를 반환하는 메소드 만들기


* 셀렉터

```groovy
package mypackage
 
import com.kms.katalon.core.testobject.ConditionType
import com.kms.katalon.core.testobject.TestObject
 
public class MySelectors {
public static final String dynamicIdPath = '//div[@id="%s"]'
 
public static TestObject getMyTestObject(String selectorType, String selectorValue) {
TestObject to = new TestObject()
to.addProperty(selectorType, ConditionType.EQUALS, selectorValue)
return to
}
}
```

* 테스트 케이스

```groovy

import com.kms.katalon.core.testobject.ConditionType
import com.kms.katalon.core.testobject.TestObject
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
 
import mypackage.MySelectors
 
String dynamicId = 'Katalon123'
String xpath = String.format(MySelectors.dynamicIdPath, dynamicId)
WebUI.click(MySelectors.getMyTestObject("xpath", xpath))
```


# 예제

하려는 동작 : runtime에서 유동적으로 값이 추가될 수 있는 List table의 추가된 값에 대한 동작이 하고싶다.

새로 추가한 내용은 테이블의 가장 마지막에 붙는다.

1. 테이블의 최대 사이즈를 구하기 위해 element를 리스트로 만든다.

```groovy
List<WebElement> CBList = WebUI.findWebElements(findTestObject('Object Repository/Page_Admin_RecruitNotice_CodeManage/checkbox_list_all'), 
    2)
sizeOfList = CBList.size()
```

2. 동적 testobject를 생성하여 xpath를 부여한다.

```groovy
TestObject testObject = new TestObject()

String xpathStr = "//*[@id=\"modalTable\"]/tbody["+ sizeOfList +"]/tr/td[1]/label/input"

testObject.addProperty('xpath', ConditionType.EQUALS, xpathStr, true)

WebUI.click(testObject)
```

* 위 동작들을 하나의 Custom Keyword 로 만들었다.

```groovy
public class dynamicTestobject {

	public static TestObject getMyTestObject(String selectorType, String selectorValue) {
		TestObject to = new TestObject()
		to.addProperty(selectorType, ConditionType.EQUALS, selectorValue)
		return to
	}
}
```


---

참고사이트

[handling static and dynamic test objects](https://medium.com/katalon-studio/handling-static-and-dynamic-test-objects-f49d04667e9d) <br>
[katalon doc](https://docs.katalon.com/katalon-studio/tutorials/handling_static_dynamic_test_objects.html#introduction)