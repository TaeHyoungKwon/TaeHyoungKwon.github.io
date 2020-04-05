---
layout: post
title: "[Cosmic Python] Preface"
description: "Cosmic Python을 읽고 중요 내용을 정리한다."
date: 2020-03-31
tags: [python, cosmicpython]
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

*   복잡한 파이썬 어플리케이션을 개발하는 사람
*   복잡한 것을 다루는 것에 고통받는 사람
*   DDD 나 클래식 어플리케이션 아키텍쳐 패턴에 대해서 모르는 사람



책 설명

*   example app 을 챕터 별로 만들면서 진행
*   TDD 사용



Frameworks and Technologies

*   Flask, SQLAlchemy, pytest, Docker, Redis 사용



이 책의 목표

*   위의 특정 기술들로 아키텍쳐를 구성해보는 것

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

*   하나의 example 프로젝트를 만들 것이고, 프로젝트를 완성 시켜 가면서 마치 페어 프로그래밍하는 것과 같이, 우리는 우리가 무엇을 하고 있고, 왜 그런지 각 스텝마다 설명할 것이다
*   그러나 패턴을 익히기 위해선, 어떻게 동작하는지에 대해서 이해해야한다.
*   코드는 깃헙에서 볼 수 있다



책과 함께 코드를 작성할 수 이쓴 3가지 방법

1.  본인 레포지토리를 생성하고, 책에서하는 것들을 따라서 한다.
2.  본인 프로젝트에 각 챕터별 패턴들을 적용해본다.
    *   high risk/high reward 
3.  Exercise for the Reader 부분을 깃헙에서 코드를 다운받아서 스스로 코드를 작성해본다



패턴들 중 일부를 자신의 프로젝트에 적용하려하는 경우 간단한 예제를 통해 작업하는 것이 안전하게 연습하는 좋은 방법이다





