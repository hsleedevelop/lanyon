---
layout: post
title: SOLID - Programming Principles
description: Programming Principles
category: algorithm
tags: [algorithm, solid]
---

**Bubble Sort - Sort algorithm**
-----

**Overview**
 - Bubble sort는 두 인접한 원소를 검사하여 정렬하는 방법이다. 시간 복잡도가 {\displaystyle O(n^{2})} O(n^{2})로 상당히 느리지만, 코드가 단순하기 때문에 자주 사용된다. 원소의 이동이 거품이 수면으로 올라오는 듯한 모습을 보이기 때문에 지어진 이름이다.

1. SRP
- 단일 책임 원칙 (Single responsibility principle)
```
한 클래스는 하나의 책임만 가져야 한다.
```

2. OCP
- 개방-폐쇄 원칙 (Open/closed principle)
```
“소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다.”
```

3. LSP
- 리스코프 치환 원칙 (Liskov substitution principle)
```
“프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다.” 계약에 의한 설계를 참고하라.
```

4. ISP
- 인터페이스 분리 원칙 (Interface segregation principle)
```
“특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다.”[4]
```

5. DIP
- 의존관계 역전 원칙 (Dependency inversion principle)
```
프로그래머는 “추상화에 의존해야지, 구체화에 의존하면 안된다.”[4] 의존성 주입은 이 원칙을 따르는 방법 중 하나
```
