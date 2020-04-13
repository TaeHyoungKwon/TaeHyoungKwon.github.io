---
layout: post
title: "[Coding Training Python] 연습문제 2. 글자 수 세기"
description: "Coding Training 문제를 풀고 정리한다."
date: 2020-04-10
tags: [codingtraining, python]
comments: true
share: true
---



## 연습문제 1. 글자 수 세기



### 출력 예

```
What is the input string? Homer
Homer has 5 characters.
```



### 제약 조건

*   출력 결과에는 입력 받은 문자열이 그대로 나타나야함
*   출력을 위해 하나의 출력문을 사용할 것
*   문자열의 길이를 구하기 위해 프로그래밍 언어에서 제공하는 내장함수를 사용할 것



### 도전 과제

*   사용자가 아무 것도 입력하지 않은 채로 엔터 키를 치면 무엇이라도 입력하라는 메시지를 나타내 보자
*   이 프로그램을 GUI 버전으로 작성하여 글자를 입력할 때마다 글자 수가 바로 바로 업데이트되도록 하라. 만일 여러분이 사용하는 언어에 GUI 라이브러리가 없다면 HTML과 javascript를 사용하라.

----



```python
import unittest
from unittest.mock import Mock, patch


def input_word():
    return input('What is the input string? ')


def count_word():
    word = input_word()
    return '{} has {} characters'.format(word, str(len(word)))


@patch('no_2.input_word', Mock(return_value='abcde'))
class Test(unittest.TestCase):
    def test_count_word(self):
        self.assertEqual(count_word(), 'abcde has 5 characters')

    def test_input_word(self):
        actual = input_word()
        self.assertEqual(actual, 'abcde')

```



---



### 회고

*   내 프로젝트를 코딩하면서, 처음으로 mocking이 이때 꼭 필요하겠구나를 느끼게된 예제이다. input() 부분을 처리할 때, 테스트를 어떻게 짜야했는지 계속 고민했는데 단순하게 mocking 처리해주면 깔끔해진다
*   바로 구현 가능한 도전 과제는 진행하고 그렇지 않은 것은 앞으로도 계속  패스하고 진행 예정