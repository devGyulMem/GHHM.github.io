# Xpath neighbor

동적 엘리먼트의 경우 미리 static한 xpath를 구하기 쉽지 않다.

그럴 때는 절대로 변하지 않는 엘리먼트를 기준으로하여 어느 방향으로 얼마만큼 떨어져 있는 지 xpath로 나타낼 수 있다.

## normalize-space

문자열에서 앞뒤 공백을 빼고(strip) 결과 스트링을 반환함

`normalize-space(string)`

### 예제
'예저평가set설명' 이라는 text 값을 가진 element를 찾는다. 만일 여러 개가 있을 경우 array로 list를 만든다.

`(.//*[normalize-space(text()) and normalize-space(.)='예제평가set설명'])`

> `(.//*[normalize-space(text()) and normalize-space(.)='예제평가set설명'])[1]`
> `(.//*[normalize-space(text()) and normalize-space(.)='예제평가set설명'])[2]`


## Axes (Sibling)

Axis는 컨텍스트 노드의 관계성을 나타난다. 주로 tree 구조에서 노드의 상대적인 위치를 나타낼 때 사용된다.

| Axis Name | Result |
|--------------------|-----------------------------------------------------------------------------------------------------------|
| ancestor | 현재 노드의 선조 노드(parent, grandparent, etc.)를 모두 선택 |
| ancestor-or-self | 현재 노드를 포함한 선조 노드를 모두 선택 |
| attribute | 현재 노드의 모든 attribute를 선택 |
| child | 현재 노드의 모든 child 노드를 선택 |
| descendant | 현재 노드의 후손 노드 (children, grandchildren, etc.)를 모두 선택 |
| descendant-or-self | 현재 노드를 포함한 모든 후손 노드를 선택 |
| following | 현재 노드의 close tag 이후 모든 document를 선택 |
| following-sibling | 현재 노드의 sibling |
| namespace | 현재 노드의 모든 namespace 노드를 선택 |
| preceding | 현재 노드가 나타나기 전 까지의 모든 노드를 선택, 단 선조 노드, attribute 노드, namespace 노드는 제외한다. |
| preceding-sibling | 현재 노드 이전의 모든 sibling 노드를 선택 |
| self | 현재 노드를 선택 |

### 예제

'예제평가set설명' 이라는 텍스트를 가진 노드중 첫 번째 노드의 이후(following) 요소들 중 td[1] 만큼 떨어져있는 노드

`(.//*[normalize-space(text()) and normalize-space(.)='예제평가set설명'])/following::td[1]`


# 이용 방법

xpath에 해당하는 element를 dynamic object로 할당하여 동작을 실행한다.

```groovy
xpath = "(.//*[normalize-space(text()) and normalize-space(.)='예제평가set설명'])/following::td[1]/label"
 
TestObject to = new TestObject("newTd")
to.addProperty("xpath",ConditionType.EQUALS, xpath)

WebUI.click(to)
```

---
관련 사이트

[xpath normalize-space](https://developer.mozilla.org/ko/docs/Web/XPath/Functions/normalize-space)

[xpath tutorial](http://zvon.org/xxl/XPathTutorial/Output/example6.html)

[xpath Axes](https://www.w3schools.com/xml/xpath_axes.asp)