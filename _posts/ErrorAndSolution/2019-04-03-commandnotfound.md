---
layout: post
current: post
title:  "Mac termianl 에서 Command not found"
navigation: True
tags: [ErrorAndSolution]
class: post-template
subtitle: "path 설정 오류"
subclass: 'post tag-getting-started'
author: mem
---

## Error
command not found on mac terminal

## Solution
Find '.bash_profile' file in home directory
and check
> export PATH=%PATH:/bin:/usr/local/bin:/usr/bin

(if you can not use 'vi' command, fine it via finder)

## Reference
* https://medium.com/@devfallingstar/macos-터미널에서-command-not-found가-계속-뜰-때-138d7fe6a3fe

