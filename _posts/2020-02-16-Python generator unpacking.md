---
layout: post
title: "[Python Snippets] Python Generator Unpacking"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-16
tags: [python, snippets, generator, unpacking]
comments: true
share: true

---



## Python Generator Unpacking



```python
a1 = ['abcde', 'bcde']
a2 = ['cde']

x, y = (list(map(len, ele)) for ele in [a1, a2])

>> x = [5, 4]
>> y = [3]

```



```python
def solution(a1, a2): 
    for a in [a1, a2]: 
        yield list(map(len,a))
        
x, y = solution(a1, a2)      

>> x = [5, 4]
>> y = [3]
```

