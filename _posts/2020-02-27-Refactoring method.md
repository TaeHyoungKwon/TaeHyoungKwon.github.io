---
layout: post
title: "[Refactoring] 메서드 정리"
description: "마틴 파울러 리팩토링 책을 읽고 패턴들을 정리한다."
date: 2020-02-27
tags: [python, refactoring]
comments: true
share: true

---


## 메서드 정리

### 서문 요약

* 핵심적인 리팩토링 기법은 코드 뭉치를 별도의 메서드로 빼내는 메서드 추출 이다.
* 메서드 내용 직접 삽입
    * 여러 묶음의 코드를 개별 메서드로 빼내고 보니 그렇게 만들어진 일부 메서드가 제 역할을 못하거나 그 메서드들을 쪼갠 방식을 바꿔야 할 때 사용
* 메서드 추출에서 가장 힘든 작업
    * 지역변수 처리를 처리하는 것인데, 주로 임시변수 때문이다.
    * 해결법
        * 임시변수를 멤서드 호출로 전환을 실시하여 없어도 되는 임시변수를 전부 제거한다.
        * 임시변수가 여러 부분에 사용될 때는 임시변수 분리를 먼저 실시하면 임시변수를 메서드 호출로 전환 기법이 더 간편해진다.
* 메서드 객체로 전환
    * 임시변수가 너무 얽혀 있어서 메서드 호출로 전환할 수 없을 때
* 매개변수로의 값 대입 제거
* 알고리즘 전환



### 메서드 추출 (Extract Method)

>   어떤 코드를 그룹으로 묶어도 되겠다고 판달될 땐, 그 코드를 빼내어 목적을 잘 나타내는 직관적 이름의 메서드로 만들자.

```python
def print_owing(amount):
    print_banner()
    
    # 세부 정보 출력
    print('{name}'.format(name))
    print('{amount}'.format(amount))
```



```python
def print_owing(amount):
    print_banner()
    print_details(amount)
    
def print_details(amount):
    print('{name}'.format(name))
    print('{amount}'.format(amount))
```



#### 동기

*   메서드가 너무 길거나 코드에 주석을 달아야만 의도를 이해할 수 있을 때, 사용한다.
*   직관적인 이름의 간결한 메서드가 좋은 이유
    1.  메서드가 적절히 잘게 쪼개져 이씅면 다른 메서드에서 쉽게 사용할 수 있다.
    2.  상위 계층의 메서드에서 주석 같은 더 많은 정보를 읽어들일 수 있다.
    3.  재정의하기도 훨씬 수월하다.
*   메서드 추출로 코드의 명료성이 향상되기만 한다면, 메서드 명이 추출한 코드보다 길어도 메서드 추출을 실시해야 한다.





#### 예제: 지역변수 사용 안 함

```python
def print_owing():
    e = _orders.elements()
    outstanding = 0
    
    # 배너 출력
    print("***********************")
    print("*******고객 외상*********")
    print("***********************")
    
    # 외상액 계산
    ...
    
    # 세부 내역 출력
    ...
        
```



```python
def print_owing():
    e = _orders.elements()
    outstanding = 0
    
    print_banner()
    
    # 외상액 계산
    ...
    
    # 세부 내역 출력
    ...
def print_banner():
    print("***********************")
    print("*******고객 외상*********")
    print("***********************")
        
```





#### 예제: 지역변수 사용

```python
def print_owing():
    e = _orders.elements()
    outstanding = 0
    
    print_banner()
    
    # 외상액 계산
    ...
    
    # 세부 내역 출력
    print("고객명: {name}".format(name))
    print("외상액: {outstanding}".format(outstanding))
    
def print_banner():
    print("***********************")
    print("*******고객 외상*********")
    print("***********************")
        
```



```python
def print_owing(name):
    e = _orders.elements()
    outstanding = 0
    
    print_banner()
    
    # 외상액 계산
    ...
    
	print_details(name, outstanding)
    
    
def print_banner():
    print("***********************")
    print("*******고객 외상*********")
    print("***********************")
    
def print_details(name, outstanding):
    print("고객명: {name}".format(name))
    print("외상액: {outstanding}".format(outstanding))
        
```





#### 지역변수를 다시 대입

```python
def print_owing(name, previous_amount):
    print_banner()
    outstanding = get_outstanding(previous_amount * 1.2)
    print_details(name, outstanding)
    
def print_banner():
    print("***********************")
    print("*******고객 외상*********")
    print("***********************")
    
def print_details(name, outstanding):
    print("고객명: {name}".format(name))
    print("외상액: {outstanding}".format(outstanding))
    
def get_outstanding(initial_value):
    result = initial_value
    e = order.elements()
    for ele in e:
        result += ele.get_amount()
    return result
```







### 메서드 내용 직접 삽입(Inline Method)

>   메서드 기능이 너무 단순해서 메서드명만 봐도 너무 뻔할 땐 그 메서드의 기능을 호출하는 메서드에 넣어버리고 그 메서드는 삭제하자.

```python
def get_rating():
    return 2 if is_more_than_five_late_deliveries else 1

def is_more_than_five_late_deliveries():
    return number_of_late_deliveries > 5
```



```python
def get_rating():
    return 2 if number_of_late_deliveries > 5 else 1
```



#### 동기

*   리팩토링의 핵심은 의도한 기능을 한눈에 파악할 수 있는 직관적인 메서드명을 사용하는 것과 메서드를 간결하게 만드는 것이다.
*   하지만 간혹 메서드명에 모든 기능이 반영될 정도로 메서드 기능이 지나치게 단순할 때가 있다. 이럴 땐 그 메서드를 없애야 한다.





### 임시변수 내용 직접 삽입(Inline Temp)

>   간단한 수식을 대입받는 임시변수로 인해 다른 리팩토링 기법 적용이 힘들 땐 그 임시변수를 참조하는 부분을 전부 수식으로 치환하자.

```python
base_price = an_order.base_price()
return (base_price > 1000)
```



```python
return (an_order.base_price() > 1000)
```



#### 동기

*   임시변수 내용 직접 삽입만 순수하게 사용되는 경우는 오직 메서드의 호출의 결괏값이 임시변수에 대입될 때 뿐이다. 이러한 임시변수는 별문제가 없으므로 내버려둬도 되지만, 만일 임시변수가 메서드 추출 등 다른 리팩토링에 방해가 된다면 임시변수 내용 직접 삽입을 적용해야 한다.





### 임시변수를 메서드 호출로 전환(Replace Temp with Query)

>   수식의 결과를 저장하는 임시변수가 있을 땐 그 수식을 빼내어 메서드로 만든 후, 임시변수 참조 부분을 전부 수식으로 교체하자. 새로 만든 메서드는 다른 메서드에서도 호출 가능하다.

```python
base_price = quantity * item_price
if base_price > 1000:
    return base_price * 0.95
else:
    return base_price * 0.98
```



```python
if base_price() > 1000:
    return base_price() * 0.85
else:
    return base_price() 0.98
...
def base_price():
    return quantity * item_price
```



#### 동기

*   임시변수는 일시적이고 적용이 국소적 범위로 제한된다는 단점이 있다.
*   임시변수를 메서드 호출로 수정하면 클래스 안 모든 메서드가 그 정보에 접근할 수 있다.
*   지역변수가 많을 수록 메서드 추출이 힘들어지므로 최대한 많은 변수를 메소드 호출로 고쳐야 한다.
*   임시변수를 메서드 호출로 전환을 적용해야 하는 가장 간단한 상황은 임시변수에 값이 한번만 대입되고 대입문을 이루는 수식에 문제가 없을 때다.



#### 예제

```python
def get_price():
    base_price = quantity * item_price
    discount_factor = 0
    
    if base_price > 1000:
        discount_factor = 0.95
    else:
        discount_factor = 0.98
    return base_price * discount_factor
```



```python
def get_price():
    discount_factor = 0
    
    if base_price() > 1000:
        discount_factor = 0.95
    else:
        discount_factor = 0.98
    return base_price() * discount_factor


def base_price():
    return quantity * item_price
```



```python
def get_price():
    return base_price() * discount_factor()

def base_price():
    return quantity * item_price

def discount_factor():
    if base_price() > 1000:
        return 0.95
    else:
        return 0.98
    
```



```python
NINETY_FIVE_DISCOUNT_FACTOR = 0.95
NINETY_EIGHT_DISCOUNT_FACTOR = 0.98

def get_price():
    return base_price() * discount_factor()

def base_price():
    return quantity * item_price

def discount_factor():
    if base_price() > 1000:
        return NINETY_FIVE_DISCOUNT_FACTOR
    return NINETY_EIGHT_DISCOUNT_FACTOR
    
```



```python
NINETY_FIVE_DISCOUNT_FACTOR = 0.95
NINETY_EIGHT_DISCOUNT_FACTOR = 0.98

def calc_price():
    return base_price() * discount_factor()

def calc_base_price():
    return quantity * item_price

def calc_discount_factor():
    return NINETY_FIVE_DISCOUNT_FACTOR base_price() > 1000 else NINETY_EIGHT_DISCOUNT_FACTOR
    
```





### 직관적 임시변수 사용 (Introduce Explaining Variable)

>   사용된 수식이 복잡할 땐 수식의 결과나 수식의 일부분을 용도에 부합하는 직관적 이름의 임시변수에 대입하자.

```python
if (platform.upper() == 'MAC' and 
    platform.upper() == 'CHROME' and 
    was_initialized and resize > 0):
    # 기능 코드
```



```python
is_mac_os = platform.upper() == 'MAC'
is_chrome_browser = platform.upper() = 'CHROME'
was_resized = resize > 0

if (is_mac_os and is_chrome_browser and was_resized):
    # 기능 코드
```



#### 동기

*   수식이 너무 복잡해져서 이해하기 힘들 수 있다. 이럴 때 임시변수를 사용하면 수식을 더 처리하기 쉽게 쪼갤 수 있다.
*   임시변수를 생각 없이 남용하면 안된다. 관련 없는 임시변수를 사용하면 메서드만 복잡해지고, 코드를 보는 사람이 이해하기 힘들어지므로 해롭다.
*   임시변수를 사용하고 싶을 때마다 더 좋은 방법이 없는지부터 생각해보자
*   메서드추출을 대신해서 할 수 있다면, 메서드 추출을 하자.
    *   이 기법을 실시했을 때, 메서드들을 객체의 다른 부분에서도 사용할 수 있기 때문이다.
*   알고리즘 내 로직이 복잡할 때, 직관적 임시 변수를 사용하여 코드 돌아가는 원리를 이해하기 쉽게 만든다.
*   나중에 로직의 복잡함이 덜해디면 나중에 언제든 임시변수를 메서드 호출로 전환 기법을 적용하면 된다.





















