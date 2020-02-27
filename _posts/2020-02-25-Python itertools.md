---
"abc def ghi 123"layout: post
title: "[Python Snippets] Python itertools"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-16
tags: [python, itertools, zip_longest]
comments: true
share: true

---



## Python Itertools

### zip_longest

```python
a = [1, 2, 3, 4]
b = [1, 2, 3, 4, 5]

print(list(zip_longest(a, b, fillvalue=0)))

>> [(1, 1), (2, 2), (3, 3), (4, 4), (0, 5)]
```



> 만약 주어진 배열의 길이가 다른 경우에, 위와 같이 사용할 수 있다.
>
> * fillvalue는 빈 값을 채워준다.
> * 만약 fillvalue에 값을 넣지 않으면, 대신 None이 들어가게 된다.

