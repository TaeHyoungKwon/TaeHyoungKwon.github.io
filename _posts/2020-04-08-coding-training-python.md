---
layout: post
title: "[Coding Training Python] 연습문제 1. 인사하기"
description: "Coding Training 문제를 풀고 정리한다."
date: 2020-04-08
tags: [codingtraining, python]
comments: true
share: true
---



## 연습문제 1. 인사하기



### 출력 예

```
What is your name? Brian
Hello, Brian, nice to meet you!
```



### 제약 조건

*   입력 부분, 문자열 연결 부분, 출력 부분을 별도로 작성할 것



### 도전 과제

*   변수를 사용하지 않는 새로운 버젼을 작성하라.
*   사람들마다 서로 다른 인사말이 나타나도록 프로그램을 작성하라



----



```python
import unittest


def hello_world():

    def _input_name():
        return input('What is your name?')

    def _get_hello_world(name):
        return 'Hello, {name}, nice to meet you!'.format(name=name)

    def _print_hello_world(string):
        return string

    return _print_hello_world(_get_hello_world(_input_name()))


class TestHelloWorld(unittest.TestCase):
    def test_hello_world(self):
        actual = hello_world()
        self.assertEqual(actual, 'Hello, Brian, nice to meet you!')


```





---



### 회고

*   1번 문제라서 그런지 문제 자체가 어렵진 않았다.
*   TDD를 처음 접해보는 사람들이 가장 쉽게 해볼 수 있는 예제.용으로도 활용할 수 있을 것 같다.