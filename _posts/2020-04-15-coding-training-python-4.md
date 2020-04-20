---
layout: post
title: "[Coding Training Python] 연습문제 4. Mad Libs"
description: "Coding Training 문제를 풀고 정리한다."
date: 2020-04-13
tags: [codingtraining, python]
comments: true
share: true
---



## 연습문제 3. 따옴표 출력



### 출력 예

```
Enter a noun: dog
Enter a verb: walk
Enter an adjective: blue
Enter an adverb: quickly
    Do you walk your blue dog quickly? That's hilarious!
```



### 제약 조건

*   한 개의 출력문만 사용하여 결과를 출력, 이때 따옴표를 출력하기 위해 적절한 확장문자를 사용해야 한다.
*   만일 사용하는 프로그래밍 언어가 문자열 보간이나 문자열 대체를 지원하느 경우, 출력문을 만드는데 활용할 것



### 도전 과제

*   입력할 수 있는 단어를 더 늘려 이야기를 확장시켜보자.
*   대답에 따라 이야기가 만들어지는 브랜칭 스토리를 구현해보자.

----



```python
import unittest
from unittest.mock import patch, Mock


def input_name():
    return input('Who said it? ')


def input_quote():
    return input('What is the quote? ')


def print_double_quote():
    return f"{input_name()} says, \"{input_quote()}\""
    

class TestDoubleQuote(unittest.TestCase):
    
    @patch('no_3.input_name', Mock(return_value='THKwon'))
    @patch('no_3.input_quote', Mock(return_value='Do code so hard.'))
    def test_print_double_quote(self):
        self.assertEqual(print_double_quote(), "THKwon says, \"Do code so hard.\"")

```



---



### 회고

*   무난한 문제였고, \ 를 붙이는 것에 대해서 다시 복습해보는 효과가 있었다.``