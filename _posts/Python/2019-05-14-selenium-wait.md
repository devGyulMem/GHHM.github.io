# Implicitly wait vs Explicitly wait

## Problem

Selenium 에서 `NoSuchElementException` 에러가 발생할 경우.

Katalon 에서도 비슷한 에러를 발견할 수 있다.
`WebELementNotFoundException`
해당 엘리먼트를 클릭하려고 했다면
`Unable to click on object`

## Reason

랜더링이 되기 전에 엘리먼트를 찾으려고해서 그렇다.

## Solution

1. WebUI.delay()
  급하거나 귀찮을 때 쓰는 방법으로.. 무조건 n초를 기다려야하기 때문에 확실하게 element를 랜더링 될거라 보장하지도 않고 느리다.
2. Implicilty wait
3. Explicitly wait


## Implicitly wait

## Explicitly wait

