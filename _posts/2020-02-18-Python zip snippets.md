---
layout: post
title: "[Python Snippets] Python Parse String to Datetime"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-16
tags: [python, snippets, datetime, parse]
comments: true
share: true

---



## Python zip

```python
In [5]: a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

In [6]: zip(a, a[1:])
Out[6]: [(1, 2), (2, 3), (3, 4), (4, 5), (5, 6), (6, 7), (7, 8), (8, 9), (9, 10)]

```

리스트 내에서 앞뒤 값을 비교 하고 싶을 때, 위와 같이 `zip` 을 이용할 수 있다.



```python
In [10]: zip(a, a[2:])
Out[10]: [(1, 3), (2, 4), (3, 5), (4, 6), (5, 7), (6, 8), (7, 9), (8, 10)]

  
In [11]: zip(a, a[3:])
Out[11]: [(1, 4), (2, 5), (3, 6), (4, 7), (5, 8), (6, 9), (7, 10)]

```

 2 or 3으로 하냐에 따라서, 만들어진 튜플의 차가 