---
layout: post
title: "[Code Wars] Count Repeats"
description: "코드 워즈 문제를 풀면서, 답을 본 문제들을 정리한다."
date: 2020-04-07
tags: [code wars]
comments: true
share: true

---



## 문제

https://www.codewars.com/kata/598ee7b6ec6cb90dd6000061/solutions/python



## 나의 풀이

* 시도

    ```python
    import unittest
    
    
    def count_repeats(txt):
        cnt = 0
        for i, char in enumerate(txt):
            if i == len(txt) - 1:
                break
            if char == txt[i + 1]:
                cnt += 1
        return cnt
        
        
    class TestCountRepeats(unittest.TestCase):
        def test_should_return_1_when_given_txt_is_abbc(self):
            txt = 'abbc'
            actual = count_repeats(txt)
            self.assertEqual(actual, 1)
    
        def test_should_return_2_when_given_txt_is_abbcca(self):
            txt = 'abbcca'
            actual = count_repeats(txt)
            self.assertEqual(actual, 2)
    
        def test_count_repeats_with_space(self):
            txt = 'ab cca'
            actual = count_repeats(txt)
            self.assertEqual(actual, 1)
    
    ```

    *   loop를 순회하면서, char가 그 다음 index 값과 같으면 consecutive 반복 이라고 보고 갯수를 증가 시켰고, 맨마지막 요소까지 loop를 돌게되면, index error 가 발생하기 때문에 그 전에 break를 하였다.
    *   차근차근 푸는 관점에서는 잘 풀었다고 볼 수 있을것 같다
    *   그러나 클린 코드의 관점에서는 무언가 깔끔하지 않고 의도를 알아보기 힘들게 코딩이 되어있다.


## 다른 사람의 풀이

1. Best Practice 1등의 풀이

    ```python
    from itertools import groupby
    def count_repeats(s):
        return len(s) - len(list(groupby(s)))
    ```

    * itertools에 groupby는 솔직히 처음보았다.

    * iterable로 부터 conservativecutive 한 key 와 그 그룹을 리턴한다.

      ```python
      
      In [31]: data = 'aaaabbccdddaaa
          '
      In [32]: temp = groupby(data)
      
      In [33]: for ele in temp:
          ...:     print(list(ele[1]))
          ...:
          ...:
      ['a', 'a', 'a', 'a']
      ['b', 'b']
      ['c', 'c']
      ['d', 'd', 'd']
      ['a', 'a', 'a']
      
      
      
      In [35]: temp = groupby(data)
      
      In [36]: for ele in temp:
          ...:
          ...:     print(list(ele)[0], list(ele)[1])
          ...:
          ...:
      a <itertools._grouper object at 0x10a787d68>
      b <itertools._grouper object at 0x10a760ef0>
      c <itertools._grouper object at 0x10a787d68>
      d <itertools._grouper object at 0x10a760ef0>
      a <itertools._grouper object at 0x10a787f28>
      ```

      



2. 그 외 풀이

    ```python
    def count_repeats(str):
        return sum(a == b for a, b in zip(str, str[1:]))
    ```

    * zip을 이용해서, 옆에 있는 값을 비교하는 방법도 있었다
    * 이 방법은 알고 있었는데 활용하지 못하였다.
    * 평소에 consecutive 관련 문제를 풀 때, 위 아래 모두 유용히 쓸 수 있을 것 같다.

## 회고

*   부족한 점
    *   주기적으로 답을 통해서 패턴들을 찾고 정리할 필요가 있다.
*   Action Item
    *   코드 워즈 문제를 풀면서 새롭게 알게된 것, 새롭게 생각하는 방식을 배우기 위해서 매일 1개씩 기록을 한다.