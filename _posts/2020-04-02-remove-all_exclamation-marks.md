---
layout: post
title: "[Code Wars] Remove all exclamation marks from the end of sentence"
description: "코드 워즈 문제를 풀면서, 답을 본 문제들을 정리한다."
date: 2020-04-02
tags: [code wars]
comments: true
share: true

---



## 문제

https://www.codewars.com/kata/57faece99610ced690000165/solutions/python



## 나의 풀이

*   시도

    ```python
    import unittest
    
    
    def remove(s):
        temp = list(s)
        for ele in s[::-1]:
            if ele.isalpha() or ele == ' ':
                break
            if ele == '!':
                temp.pop()
        return ''.join(temp)
        
        
    class TestRemove(unittest.TestCase):
        def test_should_return_sentence_without_all_of_exclamation_marks_from_the_end(self):
            s = 'Hi!'
            actual = remove(s)
            self.assertEqual(actual, 'Hi')
    
        def test_should_return_sentence_without_all_of_exclamation_marks_from_the_end_but_has_empty_space(self):
            s = 'Hi! Hi!'
            actual = remove(s)
            self.assertEqual(actual, 'Hi! Hi')
    ```

    *   끝에서 부터 문자들을 검사하여서, '!' 마크이면 복사한 리스트에서 pop 하고 그렇지 않으면, break 하고 바로 리턴하는 식으로 풀었다.

    ```python
    import unittest
    
    
    def remove(s):
        temp = list(s)
        for ele in s[::-1]:
            if ele == '!':
                temp.pop()
            else:
                break
        return ''.join(temp)
    
    
    class TestRemove(unittest.TestCase):
        def test_should_return_sentence_without_all_of_exclamation_marks_from_the_end(self):
            s = 'Hi!'
            actual = remove(s)
            self.assertEqual(actual, 'Hi')
    
        def test_should_return_sentence_without_all_of_exclamation_marks_from_the_end_but_has_empty_space(self):
            s = 'Hi! Hi!'
            actual = remove(s)
            self.assertEqual(actual, 'Hi! Hi')
    ```

    *   이후 리팩토링한 답

## 다른 사람의 풀이

1.  Best Practice 1등의 풀이

    ```python
    def remove(s):
        return s.rstrip("!")
    ```

    *   `rstip` 에 대해서 완전 처음에 파이썬을 배울 때, 사용했던 기억이 나는데, 그 이후 사용하지 않다보니 이 메소드에 대해서는 완전히 깜빡하고 있었다.

    
    
    >   `rstip([chars])`
>
    >   -   문자열 오른쪽을 제거. Chars 지정이 없으면 공백이 제거되고, 지정 되어있으면 chars의 모든 조합을 제거한다.

    ```python
In [1]: mock = 'kwontaehyoung!!@@##$$!@#$!@$#'
    
    In [2]: mock.rstrip('!@#$')
    Out[2]: 'kwontaehyoung'
    ```
    
    *   `lstrip`(왼쪽 제거) 과 `strip`(양쪽 제거) 도 있다

2.  그 외 풀이

    ```python
    import re
    def remove(s):
        return re.match(r"(.*[^!]+)\!*", s).group(1)
    ```

    ```python
    import re
    def remove(s):
        return re.search(r'^.+[^!]', s).group()
    ```

    *   위와 같이 정규표현식으로도 해결이 가능하다.

## 회고

*   부족한 점
    *   rstip을 사용해야 하는 것을 꿈에도 생각하지 못했다.
    *   정규표현식에 대해서 아직 잘 모른다
*   Action Item
    *   위의 정규 표현식에 대해서 어떻게 되는지 알아보자