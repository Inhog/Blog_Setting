---
title: SOLID
date: 2019-06-28 11:15:23
author : ho9
category :
	- Keywords
	- web-development
	- OOP
summary : SOLID(1)
thunnail : posts/http.png
---


## SOLID

---

객체지향 설계 5대 원칙인 SOLID 에 대해 알아보고, 예제를 통해 학습해보자

---

<!--more -->

### 객체지향 설계 5대 원칙 SOLID

- **SRP** ( Single reponsibility principle ) - 단일 책임 원칙
- **OCP** ( Open-closed principle ) - 개방 폐쇄 원칙
- **LSP** ( Liskov substitution principle ) - 리스코브 치환 원칙
- **ISP** ( Interface segregation principle ) - 인터페이스 분리 원칙
- **DIP** ( Dependency inversion principle ) - 의존 역전 원칙


##### 1.SRP
객체는 오직 하나의 책임을 가져야한다. ( 객체는 오직 하나의 변경의 이유만을 가져야 한다. )

예제를 통해 확인하기 전에 객체지향에서의 책임과 의존에 대해 알아야할 필요가 있다.

좋은 글이 있어서 공유합니다.
[객체지향의 올바른 이해](https://effectiveprogramming.tistory.com/entry/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5%EC%9D%98-%EC%98%AC%EB%B0%94%EB%A5%B8-%EC%9D%B4%ED%95%B4-%EC%B1%85%EC%9E%84Responsibility?category=660012)


아래의 소스예제를 보자.


**Before**

<script src="https://gist.github.com/Inhog/c117bfbaa2cbd2a85026464309b31a46.js"></script>

위의 소스의 경우, UserDataService 클래스 안에 2가지 책임 (변경의 이유 2가지)를 갖고 있다.

먼저 userData를 insert, update 하는 코드와 msg와 address를 받아서 메일을 보내는 코드를 가지고 있는데 이와 같은 경우, 메일을 보내는 코드 관련 수정사항이 발생하게 되면 클래스명을 봤을때 전혀 상관이 없는 UserDataService 클래스를 수정해야하는 상황이 발생하게 된다.

이처럼 하나의 클래스가 2가지 이상이 책임을 지니게되면 클래스의 목적이 모호해지고 ~~예를 든 경우는 코드가 간단해서 영향을 받진않지만~~ 소스가 복잡한경우에는 소스 수정시 범위가 커져서 유지보수 또한 힘들어지게된다.


**After**

<script src="https://gist.github.com/Inhog/b226df86b6ffb690375e9989987c03fe.js"></script>


위의 예를 보면, 단순하지만 하나의 클래스에 하나의 책임을 갖게끔 수정하였다. 위와같이 단일 책임 원칙을 따라서 클래스의 목적을 명확히 함으로써 구조가 복잡해지거나 수정 사항이 넓어지는 것을 예방하고 기능을 구분할 수 있게 한다.



##### 2.OCP

객체는 확장에 대해서는 개방적이고 수정에 대해서는 폐쇄적이어야 한다는 원칙이다. 즉 기존의 코드는 변경하지 않으면서 기능을 추가할 수 있도록 설계가 되어야 한다.

대표적인 예로 도형의 넓이를 구하는 소스가 있다.

**Before**

<script src="https://gist.github.com/Inhog/cf288012ddf81997e45a00d774ac2e79.js"></script>


위의 소스의 경우 width와 height를 담을 수 있는 객체를 통해 if else 문을 통해 조건에 따라 넓이를 구하는 값이 변하는 소스이다.

위와 같은 경우, 예제와 달리 분기처리할 값이 많아진다거나 계산하는 식이 변경된다면 기존 AreaCalculator클래스의 소스를 수정하여야만 한다. 이는 수정에 대해서 폐쇄적이지 못한 소스라고 볼 수 있다.

따라서 OCP를 따르기 위해, 수정해야하는 소스를 기존 코드는 변경하지않으면서 하위클래스에서 직접 수정할 수 있도록 변경한 소스가 아래의 소스이다.

**After**

<script src="https://gist.github.com/Inhog/89f804c93d22a3ad06fbda35b96c2e49.js"></script>


##### 3.LSP
