---
layout: post
title: "[Python Snippets] Python Pickle"
description: "파이썬 중요 개념들을 정리한다."
date: 2020-03-28
tags: [python, pickle]
comments: true
share: true
---



## Pickle

일반 텍스트를 파일에 저장할 때는 파일 I/O를 사용하지만, 리스트나 클래스 같은 객체들은 일반적인 파일 I/O를 통해 저장하거나 불러올 수 없고 텍스트 이외의 자료형 객체를 저장하기 위해서 pickel을 사용한다.

 Pickle 모듈은 파이썬 객체를 가져와서 문자열 표현으로 변환한다. 이 과정을 피클링(직렬화)이라고 한다. 

반대로 문자열 표현을 객체로 재구성하는 것을 언피클링(역 직렬화) 이라 한다.

파이썬 3에서 pickle 모듈을 사용하려면 바이너리 모드로 파일에 접근해야 한다.

데이터를 저장하거나 불러올 때는 파일을 바이트 형식으로 읽거나 써야한다.(wb, rb)

```python
In [1]: import pickle

In [2]: x = {}

In [3]: x["name"] = "kwontaehyoung"

In [4]: x["age"] = 31
In [6]: with open("name.pkl", "wb") as f:
   ...:		pickle.dump(x, f)
In [8]: with open("name.pkl", "rb") as f:
   ...:     name = pickle.load(f)      
    
In [9]: print(name)
{'name': 'kwontaehyoung', 'age': 31}    
```

