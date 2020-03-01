---
layout: post
title: "[Python Snippets] Python Parse String to Datetime"
description: "Code Wars 문제를 풀면서 새롭게 알게된 것들을 snippets으로 정리 한다."
date: 2020-02-18
tags: [python, snippets, zip]
comments: true
share: true

---



## Python Parse String to Datetime



```python
from dateutil.parser import parse 

date_array = [ 
  '2018-06-29 08:15:27.243860', 
  'Jun 28 2018 7:40AM', 
  'Jun 28 2018 at 7:40AM', 
  'September 18, 2017, 22:19:55', 
  'Sun, 05/12/1999, 12:30PM', 
  'Mon, 21 March, 2015', 
  '2018-03-12T10:12:45Z', 
  '2018-06-29 17:08:00.586525+00:00', 
  '2018-06-29 17:08:00.586525+05:00', 
  'Tuesday , 6th September, 2017 at 4:30pm' 
]


for ele in date_array:
    print(parser.parse(ele))
```



```python
# 결과 값

'''
2018-06-29 08:15:27.243860
2018-06-28 07:40:00
2018-06-28 07:40:00
2017-09-18 22:19:55
1999-05-12 12:30:00
2015-03-21 00:00:00
2018-03-12 10:12:45+00:00
2018-06-29 17:08:00.586525+00:00
2018-06-29 17:08:00.586525+05:00
2017-09-06 16:30:00

'''
```





### 출처

https://brownbears.tistory.com/432