---
"abc def ghi 123"layout: post
title: "[Python Snippets] Python map"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-16
tags: [python, map, lambda]
comments: true
share: true

---



## Python Itertools

### map과 lambda의 활용

```python
# 주어진 문자열을 각 단어 별로 역순으로 하여서,출력 하라.

words = 'abc 123 def xyz'.split(' ')
print(''.join(map(lambda word: word[::-1], words)))

>> 'cba 321 fed zyx'
```



