---
layout: post
title: "[System Architecture] Performance vs Scalability"
description: "System Architecture 관련 내용들을 정리한다."
date: 2020-04-29
tags: [System Architecture]
comments: true
share: true

---



## Performance vs Scalability

추가 된 리소스에 비례하여서 성능이 향상되면, 서비스는 `scalable` 하다 대개 `performance` 의 향상은 더 많은 작업 단위를 제공함을 의미하고, 데이터 셋이 커지는 경우 같이 더 큰 작업 단위를 처리 할 수 있다

* `Performance`
  * 만약 `performance` 에 문제가 있다면, single user에 대해서 시스템이 느린 것
  * 지정된 시간 간격 내 어떤 작업을 실행하는 시스템의 응답성을 나타내는 척도
* `Scalability`
  * 만약 `scalability` 에 문제가 있다면, 시스템은 single user에 대해서는 빠르지만, 큰 부하에서는 느린 것
  * 성능에 영향을 주지 않고 부하 증가를 처리하거나 가용 리소스를 즉시 늘릴 수 있는 시스템 기능을 의미





### Reference

* https://github.com/donnemartin/system-design-primer#performance-vs-scalability
* https://docs.microsoft.com/ko-kr/azure/architecture/patterns/category/performance-scalability