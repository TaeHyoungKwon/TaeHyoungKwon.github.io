---
layout: post
title: "[Code Wars] Vowel remover"
description: "코드 워즈 문제를 풀면서, 답을 본 문제들을 정리한다."
date: 2020-03-20
tags: [code wars]
comments: true
share: true

---



## 문제

https://www.codewars.com/kata/5547929140907378f9000039/train/python



## 나의 풀이

*   시도

    VOWEL set을 마든 이후, filter를 이용하였다.

    ```python
    import unittest
    
    VOWEL = {'a', 'e', 'i', 'o', 'u'}
    
    
    def shortcut(s):
        return ''.join(filter(lambda char: char not in VOWEL, s))
        
        
    class TestShortCut(unittest.TestCase):
        def test_should_delete_all_vowel_in_given_s(self):
            s = 'hello'
            actual = shortcut(s)
            self.assertEqual(actual, 'hll')

    ```
    
    *   filter를 사용하는 방법 말고도 여러가지가 있을 것이라 생각하였고, 답을 보면 여러가지 풀이법을 배울 수 있을 것이라 생각했다.

## 다른 사람의 풀이

1.  Best Practice 1등의 풀이

    ```python
    def shortcut(s):
        return s.translate(None, 'aeiou')
    ```

     이전에 몇번 보긴했는데, 그때마다 따로 정리는 해두지 않았던 부분이다.

    ```
    str.translate(table[, deletechars])
    ```

    >   #### The string translate() method returns a string where each character is mapped to its corresponding character in the translation table.

     translation table에 매핑되는 각 char를 리턴해준다. translation을 사용하기 위해서는 먼저 translation table을 먼저 생성 후 아래와 같이 사용한다.

    ```python
    In [2]: table = str.maketrans('abcde', 'ABCDE')
    In [3]: s = "Hello CodeWars"
    In [5]: translated = s.translate(table)
    
    In [6]: translated
    Out[6]: 'HEllo CoDEWArs'
    ```

    maketrans를 통해 만든 매핑 테이블을 통해서, 소문자를 대문자로 바꿔준다.

    반면, `s.translate(None, 'aeiou')` 처럼 table을 None으로 지정하면, 해당 문자를 바로 삭제하게 된다.

    문자열 내에서 모든 특정 char를 의도대로 바꿔야 할 때? 혹은 삭제 해야할 때? 사용하면 유용할 것 같다.

2.  그외 풀이

    *   ```python
        def shortcut(s):
            return ''.join(c for c in s if c not in 'aeiou')
        ```

         단순히 if 문으로도 해결 가능하다.

    *   ```python
        def shortcut( s ):
            for vowel in "aeiou":
                s = s.replace(vowel, "")
            return s
        ```

         물론 replace로도 가능한데, 위 코드는 그리 에쁘진 않은 것 같다.

    *   ```python
        import re
        shortcut = lambda s: re.sub('[aeiou]', '', s)
        ```

        ```python
        import re
        
        def shortcut( s ):
            return re.sub('[aoeui]', '', s)
        ```

         정규표현식으로도 간단히 표현 가능하다.



## 회고

*   부족한 점
    *   translate 에 대해서 잘 몰랐다
    *   정규표현식에 대해서는 아직도 잘 모른다.
*   Action Item
    *   간단한 파이썬 정규표현식 튜토리얼을 풀어보고 블로깅을 한다.
    *   translate의 간단한 사용 예만 알아봤는데, 심화적이고 디테일한 내용도 있는지 확인 후 블로깅 한다.