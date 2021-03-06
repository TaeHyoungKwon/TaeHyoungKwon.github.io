---
layout: post
title: "[Python] 클래스 속성과 정적, 클래스 메서드 사용하기"
description: "파이썬 문법 내용을 정리한다."
date: 2020-03-01
tags: [python]
comments: true
share: true
---



# 클래스 속성과 정적, 클래스 메서드 사용하기



## 클래스 속성과 인스턴스 속성 알아보기

### 클래스 속성 사용하기

```python
class className:
    attribute = value

class Person:
    bag = []
    
    def pub_bag(self, stuff):
        self.bag.append(stuff)
```


​    

```python
james = Person()
james.put_bag('책')

maria = Person()
maria.put_bag('열쇠')

print(james.bag)
print(maria.bag)

>> ['책', '열쇠']
>> ['책', '열쇠']
```

- 클래스 속성은 클래스에 속해 있으며 모든 인스턴스에서 공유한다.

- But, 위 코드에서의 한가지 문제점은 인스턴스를 가리키는 `self` 를 사용한 것인데, 사실 클래스 속성을 지칭하기에는 모호하다.

- 그래서, 클래스 속성에 접근을 할 때는 다음과 같이 클래스 이름으로 접근해야하고, 그럴때 코드가 좀 더 명확해 진다.

  ```python
  class Person:
      bag = []
      
  def put_bag(self, stuff):
      Person.bag.append(stuff)
  ```

- 참고

  속성, 메서드 이름을 찾는 순서

  - 파이썬에서는 속성, 메서드 이름을 찾을 때, 인스턴스, 클래스 순으로 찾는다. 인스턴스 속성이 없으면 클래스 속성을 찾게 되므로, james.bag, maria.bag도 문제 없이 작동한다. 그래서 겉보기에는 인스턴스 속성을 사용하는 것 같지만 실제로는 클래스 속성이다.
  - 인스턴스와 클래스에서 `__dict__` 속성을 출력해보면, 현재 인스턴스와 클래스의 숙성을 딕셔너리로 확이할 수 있다.
    - 인스턴스. `__dict__`
    - 클래스.`__dict__`

![image-123456](/images/class_method_and_static_method.png)

### 인스턴스 속성 사용하기

```python
class Person:
    def __init__(self):
        self.bag = []

    def put_bag(self, stuff):
        self.bag.append(stuff)
```

### 정리

클래스 속성

- 모든 인스턴스가 공유. 인스턴스 전체가 사용해야 하는 값을 저장할 때 사용

인스턴스 속성

- 인스턴스 별로 독립되어 있음. 각 인스턴스가 값을 따로 저장해야 할 때 사용

### 비공개 클래스 속성 사용하기

```python
class Knight:
    __item_limit = 10 # 비공개 클래스 속성
		
    def print_item_limit(self):
        print(Knight.__item_limit) # 클래스 안에서만 접근 가능
```

## 정적 메서드 사용하기

- 정적 메서드는 인스턴스의 상태를 변화시키지 않는 메서드를 만들 때 사용한다.

  - 외부상태에 영향을 끼치지 않는 순수 함수를 만들 때 사용된다.
  - 순수 함수는 부수 효과가 없고 입력 값이 같으면 언제나 같은 출력 값을 반환한다.
  - 일반 함수 처럼 작동하지만 클래스(그리고 모든 인스턴스)의 네임스페이스에 귀속된다.
  - 특정한 메서드가 주변의 다른 모든 것과 독립적일 수 있음을 잘 보여준다.
  - 모듈 대신 클래스 본체 안에 정의된 평범한 함수일 뿐이다.

  

  ```python
  class className:
      @staticmethod
      def method(arg1, arg2):
          code
  ```

  

  ```python
  class Calc:
      @staticmethod
      def add(a, b):
          print(a + b)
          
      @staticmethod
      def mul(a, b):
          print(a, b)        
          
  ```

## 클래스 메서드 사용하기

- 클래스 메서드는 정적 메서드 처럼 인스턴스 없이 호출할 수 있다는 점은 같지만, 메서드 안에서 클래스 속성, 클래스 메서드에 접근해야할 떄 사용된다.
- 특히 cls를 사용하면 메서드 안에서 현재 클래스의 인스턴스를 만들 수도 있다.

```python
class Person:
    count = 0 # 클래스 속성

    def __init__(self):
        Person.count += 1 # 인스턴스가 만들어질 때, 클래스 속성 count에 1을 더함

    @classmethod
    def print_count(cls):
        print('{0}명 생성되었습니다.'.format(cls.count)) # cls로 클래스 속성에 접근
```



------



## 참고사항

객체 인스턴스를 통해 클래스 변수를 수정하려고 시도하는 것, 즉 실수로 이름이 같은 인스턴스 변수를 만들어서 원래 클래스 변수를 가리키는 것은 파이썬 객체 지향 프로그래밍의 함정이다.

* 클래스 변수는 동일한 이름의 인스턴스 변수에 의해 가려질 수 있기 대문에 우연히 덮어써서 버그나 이상한 동작을 유발하기 쉽다.
* 정적 및 클래스 메서드는 클래스 설계에 대한 개발자의의도를 전달하고 강제한다.





## 출처

- 파이썬 코딩 도장
- Python tricks the book
- Fluent Python