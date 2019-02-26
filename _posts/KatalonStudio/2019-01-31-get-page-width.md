---
layout: post
title:  "Web UI element 2"
subtitle: "get page width, get url, get viewport height, get viewport left position, get viewport top position, get viewport width"
background: '/img/posts/katalonlogo.png'
---

# Index

* Get Page Width
* Get Url
* Get Viewport Height
* Get Viewport Left Position
* Get Viewport Top Position
* Get Viewport Width

***


# 1. Get Page Width
-----

* ## Description
현재 페이지의 넓이를 가져온다.

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |


* ## Example

```groovy

WebUI.openBrowser(GlobalVariable.G_SiteURL)

width = WebUI.getPageWidth()

WebUI.closeBrowser()

```

***

# 2. Get Url
-----

* ## Description
현재 페이지의 URL을 가져온다.

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |


* ## Returns

| Param Types | Description |
|:-----------:|:-----------:|
| String     | URL |

* ## Example

```groovy

WebUI.openBrowser(GlobalVariable.G_SiteURL)

url = WebUI.getUrl()

WebUI.closeBrowser()

```

***


# 3. Get Viewport Height/Left Position/Top Position/Width
-----

* ## Description
현재 viewport의 높이, 넓이, x, y 값을 가져온다.

* ## Parameter

| Param       | Param Type      | Mandatory | Description    |
|:-----------:|:---------------:|:---------:|:--------------:|
| flowControl | FailureHandling | Optional  | failure handlingschema를 지정하면 실행을 계속할지 중지할지 결정할 수 있다.   |


* ## Returns

| Param Types | Description |
|:-----------:|:-----------:|
| int (height)     | 현재 viewport의 높이 |
| int (left)    | 현재 viewport를 웹페이지를 기준으로 왼쪽x값 |
| int (top)    | 현재 viewport를 웹페이지를 기준으로 상단y값 |
| int (width)    | 현재 viewport의 넓이 |

* ## Example

```groovy

WebUI.openBrowser(GlobalVariable.G_SiteURL)

viewport_height = WebUI.getViewportHeight()
left_viewport = WebUI.getViewportLeftPosition()
top_viewport = WebUI.getViewportTopPosition()
viewport_width = WebUI.getViewportWidth()

```