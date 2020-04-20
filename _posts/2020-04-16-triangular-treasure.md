---
layout: post
title: "[Code Wars] Triangular Treasure"
description: "코드 워즈 문제를 풀면서, 답을 본 문제들을 정리한다."
date: 2020-04-07
tags: [code wars]
comments: true
share: true

---



## 문제

https://www.codewars.com/kata/525e5a1cb735154b320002c8/train/python



## 나의 풀이

* 시도

    ```python
    import unittest
    
    
    def triangular(n):
        return 0 if n <= 0 else sum(range(n + 1))
    
    
    class TestTriangularTreasure(unittest.TestCase):
        def test_should_return_zero_when_given_n_is_negative(self):
            n = -10
            result = triangular(n)
            self.assertEqual(result, 0)
    
        def test_should_return_zero_when_given_n_is_zero(self):
            n = 0
            result = triangular(n)
            self.assertEqual(result, 0)
    
        def test_should_return_fourty_five_when_given_n_is_nine(self):
            n = 9
            result = triangular(n)
            self.assertEqual(result, 45)
    
    
    ```
    
    *   기존에는 위와 같이 풀었다.
    *   위와 같이 풀었을 때, timeout이 발생하였다.
    *   위와 같이 풀어도 사실 답은 맞지만, timeout이 발생했다는 것은 이보다 더 효율성을 높여서 풀 수 있다는 것인데, 처음에는 방법이 잘 떠오르지 않았다.
    *   그래서, 웹서핑해서 해결할 수 있는 방법을 찾아봤는데, 방법은 매우 간단하였다.



```python
import unittest


def triangular(n):
    return 0 if n <= 0 else n * (n + 1) / 2


class TestTriangularTreasure(unittest.TestCase):
    def test_should_return_zero_when_given_n_is_negative(self):
        n = -10
        result = triangular(n)
        self.assertEqual(result, 0)

    def test_should_return_zero_when_given_n_is_zero(self):
        n = 0
        result = triangular(n)
        self.assertEqual(result, 0)

    def test_should_return_fourty_five_when_given_n_is_nine(self):
        n = 9
        result = triangular(n)
        self.assertEqual(result, 45)

```

*   `sum(range(n + 1))` 을 풀어서 설명하면, n이 10 일 때, 0부터 10까지의 합을 구하는 것이다.
*   이것은 다르게 생각하면, `n * (n + 1) / 2` 로 표현될 수 있다.
*   굉장히 간단한 것이였는데, 막상 문제를 풀 떄는 생각하지 못하였다.


## 다른 사람의 풀이

1. Best Practice 1등의 풀이

    ```python
    def triangular(n):
        return n*(n+1)/2 if n > 0 else 0
    ```

    *   else 로 0을 빼는 것이 더 깔끔해 보인다.

## 회고

*   부족한 점
    *   timeout 이 발생하였을 때, 분명히 범용적으로 사용되는 방법이 있을 것 인데, 기존에 알고 있거나, 비교적 간단한 경우가 많은 것 같은데도 막상 문제를 풀 때는 생각하지 못하였다.
*   Action Item
    *   이 문제를 시작으로 timout 관련해서, 패턴들을 정리할 필요가 있을 것 같다.