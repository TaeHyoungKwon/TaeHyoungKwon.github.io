---
layout: post
title: "[Cosmic Python] Preface"
description: "파이썬 중요 개념들을 정리한다."
date: 2020-03-30
tags: [python, setattr, getattr, delattr, hasattr, attr]
comments: true
share: true

---



# Preface

## Why Python?

*   파이썬은 가장 빠르게 성장하고 있는 프로그래밍 언어이지만, C#, Java가 겪고 있는 문제의 종류를 막 시작 중이다.
*   스타트 업들이 real business가 되면서, 웹앱과 자동화된 스크립트 들은 엔터프라이즈 소프트웨어 화 되고 있다.
*   Zen of Python 에서 `"There should be one—and preferably only one—obvious way to do it."` 을 말하지만, 불행히도, 요구사항이 복잡해진다면 항상 도움이되는 것은 아니다
*   이 책에서 다루는 기술과 패턴이 새로운 것은 아니지만, 파이썬 세계에서는 새로운 것이다. 그러나, 이 책이 DDD or Refactoring 책을 대체하진 않는다.
*   대부분 책들의 코드 예제들이 Java 또는 C++ 로 작성되는 경항이 있다보니, 해당 언어를 사용하지 않은 사용자는 익숙하지 않을 수 있기 때문에 파이썬 으로 쓰여졌다.

## TDD, DDD and Event-Driven Architecture

복잡성 관리를 위해서 3가지의 방법을 사용한다.

*   TDD
    1.  올바른 코드를 작성하게 도와준다.
    2.  리팩토링 가능하게 해준다.
    3.  걱정 없이 새로운 기능을 추가할 수 있게 해준다.
*   DDD
    *   비즈니스 영역의 훌륭한 모델을 구축하기위해, 노력할 것을 요구한다.
*   Loosely coupled(micro)services integrated via messages
    *   여러 개의 어플리케이션 이나 비즈니스 도메인에 대한 복잡성을 다루기 위한 잘 설계된 방법이다.
    *   but, Python 세계에 어떻게 맞춰서 사용할지는 아직 명확하진 않다.

이 책의 목표는 몇개의 클래식 아키텍쳐 패턴을 소개하고, TDD, DDD, event-driven services로 어떻게 서포트 할 수 있는 지를 보여주는 것이다. 우리는 이런 것들이 파이썬 방식으로 구현하기 위한 참고자료가 될 것이며, 이 분야에서 추가적인 연구를 위한 첫 단계로 사용할 수 있길 바란다.



## Who Should Read This Book

## A Brief Overview of What You'll Learn

이 책은 2가지 파트로 나뉜다.

### Part1

1.  Domain modeling and DDD (Chapters 1, 2, and 7)
2.  Repository, Service Layer, and Unit of Work patterns (Chapters 2, 4, and 5)
3.  Some thoughts on testing and abstractions (Chapter 3 and 5)



### Part2

1.  Event-driven architecture (Chapters 8-11)
2.  Command-query responsibility segregation (Chapter 12)
3.  Dependency injection (Chapter 13)



### Additional Content

*   Epilogue

## Example Code and Coding Along

