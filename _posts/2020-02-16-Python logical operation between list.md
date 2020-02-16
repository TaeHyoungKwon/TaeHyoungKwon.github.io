---
layout: post
title: "[Python Snippets] Python logical operation between list"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-16
tags: [python, snippets, logical operator, list]
comments: true
share: true

---



## Python logical operation between list



```python
def and(x, y):
    if x:
        return y
    return x
  
def or(x, y):
    if x:
        return x
    return y
```



```python
a = ['ABAR 200', 'CDXE 500', 'BKWR 250', 'BTSQ 890', 'DRTY 600']
b = ['A', 'B']

>> a and b
>> ['A', 'B']

>> a or b
>> ['ABAR 200', 'CDXE 500', 'BKWR 250', 'BTSQ 890', 'DRTY 600']
```





### 출처

https://stackoverflow.com/questions/47419342/logical-operation-between-two-boolean-lists?rq=1

