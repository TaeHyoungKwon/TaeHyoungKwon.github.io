---
layout: post
title: "[Python Snippets] Python inner function"
description: "파이썬 중요 개념들을 정리한다."
date: 2020-03-28
tags: [python, inner function, nested function, closure]
comments: true
share: true
---

## Inner fuction(내부 함수)

```python
# Inner Function
def outer():
    def inner():
        print("Nested Function")
    return innter()

>>> outer()
>>> 'nested function'
```

* 함수 내 함수
* outer를 통해서만 호출이 가능하다.



```python
def outer(x, y):
    def inner():
        print("inner local", locals())
    	return x + y
  	print("outer local", locals())
    return inner()
```

```python
outer(5, 5)

outer local {'inner': <function outer.<locals>.inner at 0x10a0c6510>, 'y': 5, 'x': 5}
inner local {'y': 5, 'x': 5}

Out[2]: 10
```

`outer` 의 `local` 은 매개변수와 `inner fuction` , `local` 은 매개변수 `x` ,`y` 인것을 알 수 있다.

외부 함수와 내부 함수는 기본적으로 네임스페이스가 공유되고, 외부함수는 지역이 내부 함수의 전역처럼 처리된다.

##Nested Function 을 사용하는 이유?

### Encapsulation

```python
def outer(num1):
    def _inner_increment(num1): # hidden from outer code
        return num1 + 1
    num2 = inner_increment(num1)
    return num1, num2
```

```python
In [5]: _inner_increment(10)
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-5-6fd60c04a62c> in <module>
----> 1 inner_increment(10)

NameError: name '_inner_increment' is not defined
```

 nested function으로 지정이되면, 외부에서는 접근 할 수 없고, `outer` 를 통해서만 접근 가능하다.

```python
In [6]: outer(10)
Out[6]: (10, 11)
```





### Closures and Factory Functions

Closure는 함수가 닫힌 내부 환경을 외부로 공개하는 것이다.



#### Closure 란?

 Closure는 퍼스트 클래스 함수를 지원하는 언어의 네임 바인딩 기술이다. 어떤 함수를 함수 자신이 가지고 있는 환경과 함꼐 저장한 레코드이다. 또한 함수가 가진 프리변수를 클로저가 만들어지는 당시 값과 레퍼런스에 맵핑하여 주는 역할을 한다.

 클로저는 일반 함수와는 다르게, 자신의 영역 밖에서 호출된 함수의 변수값과 레퍼런스를 복사하고 저장한 뒤, 이 캡처한 값들에 액세스할 수 있게 도와 준다.

```python
def generate_power(number):
    def nth_power(power):
        return number ** power # 여기서는 number를 프리변수로 볼 수 있다
    return nth_power
```

```python
In [8]: generate_power(2)
Out[8]: <function __main__.generate_power.<locals>.nth_power(power)>

In [9]: generate_power(2)(2)
Out[9]: 4

In [10]: generate_power(5)(2)
Out[10]: 25
```

 외부 함수 내에 내부 함수를 작성하고, 내부 함수를 외부로 반환할 때 내부함수에서 외부함수의 지역변수를 계속 사용하는 환경을 클로저라고 한다.

클로저 환경의 핵심은 내부 함수에서 사용하는 외부 함수의 변수인 자유 변수이다

```python
def outer(x):
    def inner(y):
        return x + y
    return inner
```

```python
inner = outer(5)
```



```python
In[18]: inner.__name__ if '__name__' in dir(inner) else 'Not Found'

Out[18]: 'inner'
```

 변수 a에 내부 함수가 저장되었는지 `__name__` 속성으로 확인해본다.



```python
In[21]: inner.__closure__[0].cell_contents
Out[21]: 5 # 외부 함수에 전달된 인자
```

 클로저 환경이 구성되면 자유 변수에 대한 정보가 속성 `__closure__` 에 저장된다. 복수의 자유변수가 생길 수 있어서, 튜플로 구성된다.



```python
In[22]: inner(10) 
Out[22]: 15
```

 내부 함수를 실행하면 자유 변수와 내부 함수를 실행할 때 전달한 값이 합산되어 결과를 반환한다.