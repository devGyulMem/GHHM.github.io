---
layout: post
current: post
title:  "Command line - file name with space"
navigation: True
tags: [ErrorAndSolution]
class: post-template
subtitle: "git discard (unstaged changes)"
background: assets/images/git.png
cover: assets/images/git.png
subclass: 'post tag-getting-started'
author: mem
---

# Probelm
폴더 명에 spcae가 들어가서 command line 에서 git add를 못함
`D:\insight_automation>git add Object Repository/Page_Admin_DashBoard_Popup/`
fatal: pathspec 'Object' did not match any files`

# Solution

* quote
`D:\insight_automation>git add "Object Repository/Page_Admin_DashBoard_Popup/"`
`D:\insight_automation>git add 'Object Repository/Page_Admin_DashBoard_Popup/'`

* 이것도 된다는데 윈도우에서는 안됨
`D:\insight_automation>git add Object\ Repository/Page_Admin_DashBoard_Popup/`

* 잘 모를때는 Tab를 유용하게 쓰자
`D:\insight_automation>git add Object`
여기 까지만 쓰고 Tab

유의점 : 파일 이름이 유니크 할 때 만 쓸 수 있으므로 될수도 있고 안 될수도 있음
