---
layout: post
title: "[Cosmic Python] Introduction"
description: "Cosmic Python을 읽고 중요 내용을 정리한다."
date: 2020-04-03
tags: [python, cosmicpython]
comments: true
share: true
---



# Introduction



## Why do our designs go wrong?

*   소프트웨어 시스템은 chaos로 가는 경향이 있다
*   Chaotic 한 소프트웨어는 기능의 동일성(sameness of function)을 특징으로 한다.
    *    소프트웨어 엔지니어가 Chaos 한 것에 대한 흔한 사례 - the Big Ball of Mud antipattern
        *   도메인 지식을 가지고 메일을 보내고 로깅을 수행하는 API handler
        *   연산은 하지 않지만 I/O는 수행하는 business logic 클래스
        *   시스템의 일부를 변경하면 위험에 처할 수 있도록 모든 것이 결합된 서비스



## Encapsulation and Abstractions

*   캡슐화(encapsulation)
    *   행동 단순화
    *   데이터 은닉



이 글에서는 먼저 첫번째 의미를 다룬다.

우리는 코드에서 수행해야할 작업을 식별하고, 해당 작업을 잘 정의된 개체 또는 함수에 제공하여 동작을 캡슐화 한다.이때 그 객체 또는 함수를 추상화라고 부른다.

```python
import json
from urllib.request import urlopen
from urllib.parse import urlencode

params = dict(q='Sausages', format='json')
handle = urlopen('http://api.duckduckgo.com' + '?' + urlencode(params))
raw_text = handle.read().decode('utf8')
parsed = json.loads(raw_text)

results = parsed['RelatedTopics']
for r in results:
    if 'Text' in r:
        print(r['FirstURL'] + ' - ' + r['Text'])
```



```python
import requests

params = dict(q='Sausages', format='json')
parsed = requests.get('http://api.duckduckgo.com/', params=params).json()

results = parsed['RelatedTopics']
for r in results:
    if 'Text' in r:
        print(r['FirstURL'] + ' - ' + r['Text'])
```



 위 코드의 동작은 같다. 그러나 두번째 코드가 더 읽기 쉽고 이해하기 쉽다. 왜냐하면, 더 높은 수준에서 추상화로 동작 하였기 때문이다.



## Layering



## The Dependency Inversion Principle



## A Place for All Our Business Logic: The Domain Model



