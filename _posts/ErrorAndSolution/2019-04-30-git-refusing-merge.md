---
layout: post
current: post
title:  "로컬 프로젝트 git push reject"
navigation: True
tags: [ErrorAndSolution]
class: post-template
subtitle: "fatal: refusing to merge unrelated histories"
background: assets/images/cover/git.png
cover: assets/images/cover/git.png
subclass: 'post tag-getting-started'
author: mem
---

# Problem

로컬에 만든 프로젝트를 github 사이트로 생성한 repo로 push할 때 아래와 같은 메시지가 뜸.

```git
! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/GHHM/HairFarming-unity.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

힌트에 써져있는대로 pull을 하면.. 리젝된다.

```git
fatal: refusing to merge unrelated histories
```

# Reason
로컬 프로젝트와 github의 remote 프로젝트는 서로 관련이 없는 프로젝트이기 때문에 기본적으로 거부한다.

# Solution

pull 할 때 `--allow-unrelated-histories` 옵션을 추가해준다.

`git pull origin 브런치명 --allow-unrelated-histories`