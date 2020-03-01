---
"abc def ghi 123"layout: post
title: "[Python Snippets] Python map"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-16
tags: [python, map, lambda]
comments: true
share: true

---



## Python map

### map과 lambda의 활용

```python
# 주어진 문자열을 각 단어 별로 역순으로 하여서,출력 하라.

words = 'abc 123 def xyz'.split(' ')
print(''.join(map(lambda word: word[::-1], words)))

>> 'cba 321 fed zyx'
```



### map과 range의 활용

```python
# 5 ~ 1 까지 역순으로 수를 만드는데, 타입을 str로 하는 리스트를 생성

In [9]: list(map(str, range(5, 0, -1)))
Out[9]: ['5', '4', '3', '2', '1']
```

