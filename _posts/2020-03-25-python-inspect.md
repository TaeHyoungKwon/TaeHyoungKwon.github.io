---
layout: post
title: "[Python] 객체의 import path 알아보기"
description: "급 알게된 python 내용들을 정리한다."
date: 2020-03-25
tags: [python]
comments: true
share: true

---



가끔 `mocking`을 위해서 `patch` 할 떄, 객체의 `import path`를 넣어야하는 경우가 있다.

이때 나는 주로 파이참의 `Copy Reference` 기능을 이용해서, 붙여넣은 후 수동 처리해주었는데, 이 방법 말고도 `import path` 에 대해서 `python code` 상으로도 확인가능 하다.

```python
from unittest import TestCase
import inspect


def hello():
    return 'Hello!'


class TestMe(TestCase):
    def test_hello(self):
        print(inspect.getmodule(hello).__name__)
        self.assertEqual(hello(), "Mock!")
   

>>> test_mock        
```



위 테스트 코드를 실행하면, `test_mock` 이라는 string이 출력된다. 저 hello 함수의 파일 명이다. 내가 기대한 것과는 달리 좀 부실하게 나오는 감도 있지만, 나중에 코드단에서 확인해야할 순간이 왔을 때, 유용하게 쓰일 일이 있을 것 같다.



```python
# Stackoverflow 예제

In [16]: import inspect
In [17]: inspect.getmodule(MyObject).__name__
Out[17]: 'lib.objects.MyObject'
```



```python
# 참고로 __file__ 로 하면 실제 path를 리턴해준다.

from unittest import TestCase
import inspect


def hello():
    return 'Hello!'


class TestMe(TestCase):
    def test_hello(self):
        print(inspect.getmodule(hello).__file__)
        self.assertEqual(hello(), "Mock!")
    
    
>>> /Users/b201903150/workspace/Codewars/code_wars/8kyu/test_mock.py
```



### Reference

[Stackoverflow](https://stackoverflow.com/a/18712381)

