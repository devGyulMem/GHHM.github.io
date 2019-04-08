---
layout: post
current: post
title:  "Git discard"
navigation: True
tags: [ErrorAndSolution]
class: post-template
subtitle: "git rebase conflict"
background: assets/images/git.png
cover: assets/images/git.png
subclass: 'post tag-getting-started'
author: mem
---

# Problems
파일을 이것저것 옮기다가 실수해서 다른 살마의 파일을 옮겨버린거같다..

`git checkout -- <Filename>` 으로 해결하려고 했는데 삭제된 파일만 복구하는 것에 실패(아마도 폴더 이름이 space가 있어서 실패한거같다... 협업 중이라 내가 임의로 폴더 명을 바꿀 수 없어서 어쩔 수 없음 ㅠ)

그래서 뭘 실수 했는지 몰라서 그냥 로컬은 다 날리기로 했따 ㅠ

git desktop이나 편집기에 내장된 툴에는 discard라는 기능이 따로 있던데 커멘드라인에는 따로 없어서 아래와 같은 방법으로 해줘야함

# Solution

언스테이지 상태의 변경사항(unstaged changes)을 날리고 싶을 때

* 변경 사항을 다 날림. 그러나 추가된 파일의 경우 git status에 그대로 남아있다.

`git checkout -- .`

* 추가된 파일도 날리고 싶으면

`
git clean -df
git checkout -- .
`