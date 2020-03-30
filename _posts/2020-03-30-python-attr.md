---
layout: post
title: "[Python Snippets] Python setattr, getattr, delattr, hasattr"
description: "파이썬 중요 개념들을 정리한다."
date: 2020-03-30
tags: [python, setattr, getattr, delattr, hasattr, attr]
comments: true
share: true

---

## setattr

`setattr(object, name, value)`

*    object에 존재하는 속성의 값을 바꾸거나, 새로운 속성을 생성하여 값을 부여한다.

```python
class SampleClass:
    def __init__(self, num):
        self.num = num
```

```python
>>> instance = SmapleClass(1)
>>> instance.num
1
```



```python
>>> setattr(instance, 'num', 2)
>>> instance.num
2
```

<기존 속성의 값을 바꾸는 경우>



```python
>>> setattr(instance, 'another_num', 5)
>>> instance.another_num
5
```



## getattr

`getattr(object, name[, default])`

*   object에 존재하는 속성의 값을 가져온다.

```python
class SampleClass:
    def __init__(self, num):
        self.num = num
```



```python
>>> instance = SmapleClass(1)
>>> instance.num
1
```



```python
>>> getattr(instance, 'num')
1
```

<기존 속성의 값을 가져오는 경우>



```python
>>> c.x
1
```

<getattr을 사용하지 않고, c.x를 하여도 동일한 결과>



```python
>>> getattr(instance, 'not_exist_attr')
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-15-d00562231f3e> in <module>
----> 1 getattr(instance, 'not_exist_attr')

AttributeError: 'SampleClass' object has no attribute 'not_exist_attr'
```

<기존에 존재하지 않는 속성을 가져오려 하는 경우(기본 값이 없을 때)>



```python
>>> getattr(instance, 'not_exist_attr', 10)
>>> 10
```

<기존에 존재하지 않는 속성을 가져오려 하는 경우(기본 값이 있을 떄)>



## delattr

`delattr(object, name)`

*    object에 존재하는 속성을 제거한다.

```python
class SampleClass:
    def __init__(self, num):
        self.num = num
```

```python
>>> instance = SmapleClass(1)
>>> instance.num
1
```



```python
>>> delattr(instance, 'num')

>>> getattr(instance, 'num')
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-19-bed1e7fa7976> in <module>
----> 1 getattr(instance, 'num')

AttributeError: 'SampleClass' object has no attribute 'num'
```

<기존 속성을 제거하는 경우>



```python
>>> del instance.num

>>> getattr(instance, 'num')
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-23-bed1e7fa7976> in <module>
----> 1 getattr(instance, 'num')

AttributeError: 'SampleClass' object has no attribute 'num'
```

<delattr을 사용하지 않고 del c.x를 하여도 동일한 결과를 얻는다.>



```python
>>> delattr(instance, 'not_exist_attr')
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-24-55223dcbb687> in <module>
----> 1 delattr(instance, 'not_exist_attr')

AttributeError: not_exist_attr
```

<기존에 존재하지 않는 속성을 제거하려는 경우>



## hasattr

`hasattr(object, name)`

*    object의 속성 존재를 확인한다.
*   argument로 넘겨준 object에 name의 속성이 존재하면 True, 없으면 False를 반환한다.
*   내부적으로 `getattr(object, name)` 을 이용하는데 해당 함수 수행시 exception이 발생하는지 하지 않는지를 통해 판단

```python
class SampleClass:
    def __init__(self, num):
        self.num = num
```

```python
>>> instance = SmapleClass(1)
>>> instance.num
1
```



```python
>>> hasattr(instance, 'num')
True
```

<해당 object에 name 속성이 존재하는 경우>





```python
>>> hasattr(instance, 'num')
False
```

<해당 object에 name 속성이 존재하지 않는 경우>



### REFERENCE

*   https://technote.kr/248
*   https://technote.kr/249
*   https://technote.kr/250
*   https://technote.kr/251

