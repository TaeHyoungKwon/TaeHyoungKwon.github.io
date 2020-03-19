---
layout: post
title: "[Code Wars] Sort the comments"
description: "코드 워즈 문제를 풀면서, 답을 본 문제들을 정리한다."
date: 2020-03-19
tags: [code wars]
comments: true
share: true

---



## 문제

https://www.codewars.com/kata/58a0f18091e53d2ad1000039





## 나의 풀이

*   시도

    단순히 정렬하면 되는 것 아닌가? 라는 생각에 바로 정렬해서 return 하였다.

    ```python
    import unittest
    
    
    def sort_ranks(ranks):
        return sorted(ranks)
        
        
    class TestSortRanks(unittest.TestCase):
        def test_sort_ranks(self):
            ranks = ['1.1', '1', '1.1.1.1', '1.1.1']
            actual = sort_ranks(ranks)
            self.assertEqual(actual, ['1', '1.1', '1.1.1', '1.1.1.1'])
    
    ```

    ```shell
    ['1', '10', '2', '3', '4', '5', '6', '7', '8', '9'] should equal ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10']
    ```

    *   결과는 위의 테스트가 깨지는 현상이 발견
        *   10이 넘어 갈 경우, 문제가 의도한 것과 순서가 달라진다.(string 기준으로 하기 때문에)
        *   어떤 식으로 문제를 풀까 고민해보다가 시간이 너무 지체 된다고 생각되어서, 답을 보았다.



## 다른 사람의 풀이

1.  Best Practice 1등의 풀이

    ```python
    from distutils.version import LooseVersion
    
    
    def sort_ranks(ranks):
        return sorted(ranks, key=LooseVersion)
    ```

    `distutils` 는 파이썬 모듈을 설치하는데 사용이되는 모듈이다. 사실 이 모듈은 한번도 사용해보지 않았다.  구글링해서 모듈의 용도를 보고 나서 왜 굳이 이걸 썼을까? 라는 생각이 들었다.

    그러나 `LooseVersion` 을 찾아보고 나서는 이해를 할 수 있게 되었다.`LooseVersion` 은 `Version numbering` 을 해준다. `numeric components` 는 `numerically` 하게, `alphabetic components` 는 `lexically` 하게 비교해준다.

    따라서 `sorted` 의 `key` 를 `LooseVersion` 로 하면서, 위의 기준대로 정렬이 가능하다.

    

2.  그외 풀이

    ```python
    def sort_ranks(ranks):
      return sorted(ranks, key=lambda s: tuple(int(x) for x in s.split('.')))
    ```

    `sorted` 의 `key` 를 `lambda` 를 통해서 표현했다. 위와 같이 했을 때, 만들어지는 `tuple` (int element를 가짐)을 기준으로 정렬이 될 것이기 때문에 의도대로 정렬이 될 것 이다.

    

    ```python
    def sort_ranks(ranks):
        return sorted(ranks, key=lambda x: map(int, x.split('.')))
    ```

     `sorted` 의 `key` 를 `lambda` 를 통해서 표현하는데, 위와 다르게 `map` 을 이용 하였다. 위와 거의 동일한 방식인데, 위보다는 아래가 더 깔끔하고 명확한 것 같다.



## 회고

*   부족한 점
    *   Python 정렬 방법에 익숙하지 못하다. (아직도??)
    *   `Distutils` 에 대해서 알아 볼 필요가 있을 듯하다
*   Action Item
    *   `Distuils` 모듈의 `LooseVersion` 의 구현 부분을 살펴본 후 포스팅 한다.
    *   파이썬으로 정렬하는 방법에 대해서 총정리 관련 포스팅을 한다.(특히 key를 활용한 다양한 예제들)