---
title:  "[Java] 컬렉션 프레임워크"
excerpt: "자바의 Collection framework의 개념과 하위요소"

categories:
  - Java
tags:
  - 자바 문법
  - 자바
last_modified_at: 2020. 5. 26. 14:13
---

## 컬렉션 프레임워크 (Collection's'  Framework) 

' 데이터 군(group) '을 저장하는 클래스들을 '표준화'한 설계.

Collections는 다수의 데이터(데이터 그룹)를,  
Framework는 표준화된 프로그래밍 방식을 의미한다.

※ Java API 문서에서는 컬렉션 프레임워크를 '데이터 군(group)'을 다루고 표현하기 위한 단일화된 구조(architecture)라 정의

*출처 : Java의 정석 제 3판 남궁성 저


프로그램 구현에 필요한 자료구조와 알고리즘을 구현해 놓은 라이브러리  
(개발에 소요되는 시간을 절약하고 최적화된 라이브러리를 사용할 수 있다)

java.util 패키지에 구현되어 有

Collection 인터페이스와 Map 인터페이스 로 구성된다


### Collection 인터페이스

하위에 List 인터페이스와 Set 인터페이스로 구성

![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Collection%20framework/1.png?raw=true)  
[<U>사진 출처</U>](출처 : https://www.benchresources.net/collection-interface-in-java/)

<br/>

#### List 인터페이스

 ArrayList, Vector, LinkedList, Stack, Queue 등 有

#### Map 인터페이스

쌍으로 이루어진 객체를 관리하는데 필요한 여러 메서드 有  

Map을 사용하는 객체는 Key - Value  쌍으로 되어있고, Key는 중복될 수 X

HashSet, TressSet 등의 구현 클래스 존재

<br/>
<br/>

### Java API (Application Programming Interface) 

Java 시스템을 제어하기 위해서 자바에서 제공하는 ' 명령어 '들.  
즉, 자바를 사용하여 쉽게 구현할 수 있도록 한 클래스 라이브러리의 집합이다. 

Java SE(JDK)를 설치하면 자바 시스템을 제어하기 위한 API를 제공한다.  
자바 개발자들은 자바에서 제공한 API를 이용해서 자바 애플리케이션을 만들게 된다.

패키지 java.lang.\*의 클래스들도 자바에서 제공하는 API 중의 하나라고 할 수 있다.

즉, 자바라는 언어를 사용하여 사용자의 부담을 최소화하는 반면에  
입출력, 화면 구성, 이미지, 네트워크와 같이 복잡하지만 필요한 클래스들을  
미리 구현하여 사용자가 쉽게 구현하도록 하는 API이다.

이러한 자바 API는 하나의 커다란 클래스 계층구조로 설계되어 있다.

[<U>Collections framework</U>](https://docs.oracle.com/javase/7/docs/technotes/guides/collections/overview.html)

(아래 글은 Java API 문서에 있는 컬렉션 프레임워크에 대한 개념을 번역한 글이다.)

<br/>

Java 플랫폼에는 컬렉션 프레임 워크가 포함되어 있습니다 .

컬렉션 프레임 워크는 컬렉션을 표현하고 조작하기위한 통합 아키텍처로,  
구현 세부 사항과 독립적으로(!) 컬렉션을 조작 할 수 있습니다.

<br/>

### 컬렉션 프레임 워크의 장점

- 자료구조와 알고리즘을 제공하여 프로그래밍 노력을 줄이기에 직접 작성할 필요가 없습니다.

- 자료 구조 및 알고리즘의 고성능 구현을 제공하여 프로그램 성능을 향상시킵니다. 

- 각 인터페이스의 다양한 구현은 서로 호환 가능하므로 구현을 전환하여 프로그램을 조정할 수 있습니다.

- 컬렉션을 앞뒤로 전달할 공용 언어를 설정하여 관련없는 API 간의 상호 운용성을 제공합니다 .

- 여러 임시 수집 API를 학습하도록 요구함으로써 API 학습에 필요한 노력을 줄입니다.

- 임시 컬렉션 API를 생성하지 않아도 되므로 API를 설계하고 구현하는 데 드는 노력이 감소.

- 컬렉션 및 알고리즘을 조작 할 수있는 표준 인터페이스를 제공하여 SW의 재사용을 촉진 합니다.


