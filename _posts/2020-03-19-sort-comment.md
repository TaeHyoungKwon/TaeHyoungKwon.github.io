---
layout: post
title: "[Code Wars] Greek Sort"
description: "코드 워즈 문제를 풀면서, 답을 본 문제들을 정리한다."
date: 2020-03-30
tags: [code wars]
comments: true
share: true

---



## 문제

https://www.codewars.com/kata/56bc1acf66a2abc891000561/solutions



## 나의 풀이

*   시도

    *   단순히 문자열 끼리 비교하면 될 것이라고 생각했다.

    ```python
    import unittest
    
    
    def greek_comparator(lhs, rhs):
        print(lhs, rhs)
        if lhs > rhs:
            return 1
        elif lhs < rhs:
            return -1
        else:
            return 0
        
        
    class TestGreekComparator(unittest.TestCase):
    
        def test_should_return_0_when_given_lhs_and_rhs_is_same(self):
            lhs, rhs = 'psi', 'psi'
            actual = greek_comparator(lhs, rhs)
            self.assertEqual(actual, 0)
    
        def test_should_return_1_when_given_lhs_is_less_than_rhs(self):
            lhs, rhs = 'upsilon', 'rho'
            actual = greek_comparator(lhs, rhs)
            self.assertEqual(actual, 1)
    
        def test_should_return_negative_1_when_given_rhs_is_less_than_lhs(self):
            lhs, rhs = 'alpha', 'beta'
            actual = greek_comparator(lhs, rhs)
            self.assertEqual(actual, -1)
    
    ```

    *   문제를 보았을 때, '0', 'positive number', 'negative number'를 반환하도록 되어있어서, 위와같이 처리하면 될 줄 알았는데, 최종 테스트에서 틀리는 것이 계속 나와서, 그냥 답을 보았다.
    *   8Kyu 문제들 중에 특히 문제는 쉬운데, 조건이 제대로 안나와 있어서 혹은 테스트가 거지같이(?) 쓰여있어서, 제대로 못푸는 문제가 꽤 되는 것 같다.. ~~내 2점...~~



## 다른 사람의 풀이

1.  Best Practice 1등의 풀이

    ```python
    def greek_comparator(lhs, rhs):
        return greek_alphabet.index(lhs) - greek_alphabet.index(rhs)
    ```
    
    *   greek_alphabet을 사용해야하는 것을 문제에서 제대로 명시 안해줬는데.. 답을 보고 좀 짜증이 났다
    *   하지만, 위와 같은 접근법은 생각을 못했는데 좋은 접근 법을 배울 수 있었다.

    

    

2.  그외 풀이

    ```python
    def greek_comparator(lhs, rhs):
        return cmp(greek_alphabet.index(lhs), greek_alphabet.index(rhs))
    ```

    *   cmp 라는 built-in 모듈을 사용한다.
    *   C 에서 strcmp 같은 역할을 하는 것 같은데, 아쉽게도 python3 버젼에서는 사라졌고, 위 Best practice 방법이 가장 적절한 것 같다.

## 회고

*   부족한 점
    *   부족한 점이라기 보다는 python3에서 strcmp 함수 쓰는 것과 같은 효과를 내려면 문자열 index 간에 차를 구하면 된다는 사실을 알게 되었다.
*   Action Item
    *   딱히 없다