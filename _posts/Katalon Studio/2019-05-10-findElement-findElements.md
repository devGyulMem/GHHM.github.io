
# Selenium
# find element vs find elements


## find element

WebElement 하나를 반환하고, 여러 개가 있을 경우 첫 번째 element를 반환한다.

`WebElement elementName = driver.findElement(By.LocatorStrategy("LocatorValue"));`

Locator Strategy
- ID
- Name
- Class Name
- Tag Name
- Link Text
- Partial Link Text
- XPATH

## find elements

WebElement 리스트를 반환한다. 해당되는 element가 없을 경우 empty list를 반환한다.

`List<WebElement> elementName = driver.findElements(By.LocatorStrategy("LocatorValue"));`


## 차이점

| Find Element | Find Elements |
|-------------------------------------------------------------------------|--------------------------------------------------------|
| 같은 locator에 해당하는 element가 여러 개 있을 경우 첫 번째 요소를 리턴 | web element들의 리스트를 리턴 |
| locator에 해당하는 element가 없을 경우 NoSuchElementException 발생  | 맞는 element가 없을 경우 빈 리스트를 반환 |
| 오직 하나의 web element를 찾음 | locator에 맞는 element 모음을 찾음 |
|  | 각각의 web element는 어레이 처럼 0부터 인덱싱되어있다. |


[참고사이트](https://www.guru99.com/find-element-selenium.html)