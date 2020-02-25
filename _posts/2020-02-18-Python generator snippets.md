---
layout: post
title: "[Python Snippets] Python Generator Snippets"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-16
tags: [python, snippets, generator]
comments: true
share: true

---



## Python Generator

```python
def in_asc_order(arr):
    return next((False for i in range(1, len(arr[1:])+1) if not arr[i] > arr[i-1]), True)
```

> 위 코드에 대한 섦명(작성 중)
>
> * 