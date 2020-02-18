---
layout: post
title: "[Git] git log"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-16
tags: [python, snippets, datetime, parse]
comments: true
share: true

---



## git log

> - 커밋 로그를 보여준다.



* `git log -S <string>`
  * 코드 변경 찾을 때, `-S` 옵션을 사용한다.
* `git log --grep <string>`
  * 커밋의 title로 검색할 때 `--grep`  옵션을 사용한다.
* `git log --oneline`
  * 커밋을 한줄로 보여준다.