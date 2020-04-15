---
layout: post
title: "[Coding Training Python] 연습문제 3. 따옴표 출력"
description: "Coding Training 문제를 풀고 정리한다."
date: 2020-04-13
tags: [codingtraining, python]
comments: true
share: true
---



## 연습문제 3. 따옴표 출력



### 출력 예

```
What is the quote? These aren't the droids you're looking for
Who said it? Obi-Wan Kenobi
Obi-Wan Kenobi says, "These aren't the droids you're looking for."
```



### 제약 조건

*   한 개의 출력문만 사용하여 결과를 출력, 이때 따옴표를 출력하기 위해 적절한 확장문자를 사용해야 한다.
*   만일 사용하는 프로그래밍 언어가 문자열 보간이나 문자열 대체를 지원하느 경우라도 이 기능들을 사용 하지 말고 그냥 문자열 연결을 사용할 것



### 도전 과제

*   7자엥서 데이터 리스트에 대해서도 연습하게 될 것 이다. 앞의 프로그램을 수정하여 사용자로부터 입력을 받는 대신 인용구오 ㅏ이과 관련된 내용을 담는 ㅏㅈ료구조를 만들어 모든 내용을 앞의 출력 예와 같이 나타내 보자. 맵 형태의 배열을 사용해도 좋을 것 이다.

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