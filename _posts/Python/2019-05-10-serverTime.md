---
layout: post
cover: assets/images/cover/pythonlogo.png 
title:  "서버시간 알아내기"
navigation: True
tags: [Python]
class: post-template
subtitle: "도메인과 시간 동기화 / reqeust로 서버시간 구하기"
background: assets/images/cover/pythonlogo.png 
subclass: 'post tag-getting-started'
author: mem
---

# 자동화 폼 제출

request를 보내서 서버 시간을 알아오는 방법도 있지만 아무래도 latancy 때문에 정확하지 않다.

서치해 본 결과 내 컴퓨터를 도메인 주소의 시간과 동기화 하는 방법이 있다는걸 알게되었다.

## 도메인 ip주소 알아내기

`nslookup`

[관련사이트](https://m.blog.naver.com/PostView.nhn?blogId=ltehoc&logNo=220840545215&proxyReferer=https%3A%2F%2Fwww.google.com%2F)

## 도메인 주소와 시간 동기화
[python 시간](https://medium.com/@whj2013123218/%EC%88%98%EA%B0%95-%EC%8B%A0%EC%B2%AD-%EB%B0%8F-%ED%8B%B0%EC%BC%80%ED%8C%85-%EC%84%B1%EA%B3%B5%EC%9D%84-%EC%9C%84%ED%95%9C-tip-%EB%B0%8F-python-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8-facc9107abc7)

## 사용 library
- pyautogui (https://anaconda.org/conda-forge/pyautogui)
- time
- datetime

pyautogui는 마우스, 키보드 자동조작 모듈임. 화면의 x,y 좌표를 클릭해주는 click 메소드를 지원하고있다.

이걸로는 원하는 결과를 얻을 수 없기 때문에 제출 버튼의 xpath를 기반으로 클릭하도록 하겠다. selenium을 사용하겟음.

- selenium

### simple click code

```python
import datetime as dt
improt time

end = False
while not end:
    time = dt.datetime.now()
    if time.second>=59 and time.microsecond>500000:
        btn_submit.click()  #폼제출
        #btn은 따로 가져와야함
    else :
        time.sleep(0.1)
        print(time)
        
```

### simple find element code

``` python
from selenium import webdriver as wd

form_url = ''

driver = wd.Chrome(executable_path='./chromedirver')

driver.get(form_url)

btn_submit = driver.find_element_by_class('submitBtn')

driver.find_element(By.class = 'submitBtn')

```