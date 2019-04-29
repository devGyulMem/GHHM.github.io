---
layout: post
cover: assets/images/katalonlogo.png 
title:  "Selenium - csp disable"
navigation: True
tags: [Katalon Studio]
class: post-template
subtitle: "정적 및 동적 테스트 오브젝트 핸들링"
background: assets/images/katalonlogo.png 
subclass: 'post tag-getting-started'
author: mem
---

# Selenium에서 csp disable하기

## 

```
[0429/171034.947:INFO:CONSOLE(14)] "Refused to load the script 'https://cm.g.doubleclick.net/pixel?google_nid=twitter_dbm&google_cm&tpm_cb=partnerIdSyncComplete&_=1556525434556' because it violates the following Content Security Policy directive: "script-src https://ssl.google-analytics.com https://twitter.com 'unsafe-eval' https://*.twimg.com https://api.twitter.com https://analytics.twitter.com https://publish.twitter.com https://ton.twitter.com https://syndication.twitter.com 'nonce-RPoIsJapiR0m82ekx184UQ==' https://www.google.com https://platform.twitter.com https://www.google-analytics.com blob: 'self'". Note that 'script-src-elem' was not explicitly set, so 'script-src' is
used as a fallback.
```


[참고사이트](https://nomo.asia/376)