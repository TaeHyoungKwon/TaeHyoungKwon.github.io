---
layout: post
title: "[Python Snippets] Python Parse String to Datetime"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-16
tags: [python, snippets, datetime, parse]
comments: true
share: true

---



## Python underscore

`ingle_trailing_underscore_`: used by convention to avoid conflicts with Python keyword, e.g.

```python
Tkinter.Toplevel(master, class_='ClassName')
```



```python
max_ = max([1,2,3,4,5])
```

극단적인 경우로 위와 같이 예를 들었는데, 사실 위와 같이 하지 않고, `max_val` 이라고 했을 때, 큰 의미의 차이가 없다면, 위와 같은 경우는 왠만하면 자제 되어야 한다.

> 정말 어쩔 수 없는 경우에만 알아두고 사용여부를 고려해 보자.



### 출처

[PEP8](https://www.python.org/dev/peps/pep-0008/#id34)

