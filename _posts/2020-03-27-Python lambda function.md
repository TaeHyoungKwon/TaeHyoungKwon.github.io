---
layout: post
title: "[Python Snippets] Python lambda function"
description: "파이썬 중요 개념들을 정리한다."
date: 2020-03-27
tags: [python]
comments: true
share: true

---



## 람다 함수

>  익명 함수(anonymous function)은 함수 정의문이 없으므로 lambda라는 키워드를 사용하고 콜론(:) 을 경계로 앞에는 매개변수, 뒤에는 표현식을 정의한다. 표현식 대신 문장으로 표현하면 예외가 발생하므로 반환 값을 처리하는 return문이 필요 없고 표현식을 실행된 결과가 자동으로 반환되는 것을 알 수 있다.

 람다 함수로 정의한 함수가 필요한 이유는 직접 정의해서 바로 사용하는 것보다 좋은 경우가 있기 때문이다



### 1. 람다 함수의 정의

(1) 함수 정의문과 람다 함수의 변수 할당 비교

```python
def add(x, y):
    return x + y
print(add(10,10))

>> 20
```



```python
a = lambda x, y: x + y
print(a(10, 10))

>> 20
```



(2) 람다 함수도 function class 객체 여부 확인

```python
lam = set(dir(lambda x, y : x + y))
print(type(lambda x, y : x + y))

obj = set(dir(object))

for i in (lam - obj):
    print(i)
```



### 2. 즉시 실행 함수(Immediately - invoked function expression)

### 3. List comprehension 에서 람다 함수 사용하기

