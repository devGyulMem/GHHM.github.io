---
layout: post
title:  "[파이썬] loop 안에서 딕셔너리 아이템 삭제하기"
navigation: True
tags: [Python]
class: post-template
subtitle: "RuntimeError: dictionary changed size during iteration"
subclass: 'post tag-getting-started'
author: mem
---


# Code

```python
list_to_remove = dictionary.keys()
for item in list_to_remove:
    if item.isalpha() == False:
        del dictionary[item]
    elif len(item) == 1:
        del dictionary[item]
dictionary = dictionary.most_common(3000)
```

# Problem

`RuntimeError: dictionary changed size during iteration`

# Reason

for loop를 돌면서 dictionary가 변화하기 때문.

```python
list_to_remove = dictionary.keys()
```

*BUT* python 3.x 부터는 keys() 가 iterator를 반환하기 때문에 솔루션의 방법으로 써야한다.


# Solution

```python
list_to_remove = list(dictionary)
```