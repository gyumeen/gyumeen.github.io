---
title: "[Spring] 스프링 프레임워크"
toc: true
toc_sticky: true
excerpt: "스프링 프레임워크에 대한 기본 개념"

categories: 
  - Spring
tags: 
  - 스프링
last_modified_at: 2020. 5. 23. 14:31 
---

## Toby님의 스프링(Spring) 프레임워크 정의

"자바(Java) 엔터프라이즈(Enterprise) 개발을 편하게 해주는  
오픈소스 경량급(lightweight) 애플리케이션 프레임워크"

Spring  =  Application Framework  
(애플리케이션 프레임워크 ≠ 프레임워크)

<br/>

### Framework

프로그래밍 언어로 개발을 할 때,  
사람마다 개발 패턴이나 방식이 각기 다를 수 있다.

서로 개발하는 스타일이 다르면  
나중에 프로젝트를 합치기도 어렵고  
상대방의 코드를 읽기도 어려움.

여러 개발자들이 하나의 프로젝트를 작업할 때,  
어떠한 식으로 작업하자라는 개발 방식이 정해진  
도구를 프레임워크라 한다.

<br/>

Application의 특정 계층(hierarchy)에서  
주로 동작하는 한 가지 기술 분야에 집중  

(일반적으로 프레임워크 or 라이브러리는  
특정 업무 분야나 한 가지 기술에 특화된 목표 有)

<br/>

### Application Framework  

Application의 전(All) 영역을 포괄하고  
지원하는  범용적인(종합적인) 프레임워크

애플리케이션 프레임워크는  
특정 계층, 기술, 업무 분야에 국한되지 X

<br/>

### Spring Framework가 Application Framework인 이유 

단순히 여러 계층의 다양한 기술을 그저 한데 모아뒀기 때문이 아니다.

Application 전 영역을 관통하는  
일관된 프로그래밍 모델과 핵심 기술을 바탕으로  
각 분야의 특성에 맞는 필요를 채워주고 있기 때문에  
Application을 빠르고 효과적으로 개발 가능한 것.

<br/>
<br/>

- <U>Spring은 단순히  
  MVC 프레임워크 or JDBC / ORM 지원 프레임워크가 X</U>

  (스프링이 다루는 일부 영역만 본 실수)

<br/>

- <U>Spring은 단순히  
  IoC / DI 프레임워크 or AOP 툴이 X</U>  

  (스프링이 제공하는 핵심 기술만 주목한 실수)

<br/>

- <U>AOP와 OOP는 상호 배타적 X (Vol. 1 746p)</U>

  AOP(관점 지향 프로그래밍):  
  객체지향 기술의 한계와 단점을 극복하도록 도와주는 보조적인 프로그래밍 기술

<br/>
<br/>  

출처 : 토비의 스프링 3.1 Vol. 1 p.713 ~

----------------------------------------------------------------------------------------------------

<br/>
<br/>

Java는 객체지향 프로그래밍 언어이다.  
Spring은 이런 Java 언어 기반의 프레임워크다. 

Spring은 객체지향 언어가 가진  
강력한 특징(특히 '다형성')을 극대화하여  
좋은 객체지향 애플리케이션을 개발할 수 있도록  
지원하는 프레임워크다.

## Spring 프레임워크의 특징 1

- <U>경량의 컨테이너</U>로써 자바 객체를 직접 관리  
- <U>POJO</U>(Plain Old Java Object) 방식의 프레임워크  
- <U>IoC</U>(Inversion of Control : 제어의 역전) 지원  
- <U>DI</U>(Dependency Injection) 지원  
- <U>AOP</U>(Aspect-Oriented Programming) 지원
- <U>iBATIS, myBATIS, Hibernate</U> 등의 데이터베이스 라이브러리 지원

## Spring 프레임워크의 특징 2  

<U>자바 파일에서 자바 코드를 줄일 수 있다.</U>  

물론 작업량이 굉장히 많이 줄어드는 게 아니다.  
다만 중복되는, 반복되는 코드를 해소할 수 있다. 

<U>반복되는 작업을 줄일 수 있어 기능 개발에 집중할 수 있다.</U>

자바 파일에서 자바 코드를 없애고  
자바 코드로 동작하기 위해 필요한 정보들을  
XML이나 애노테이션으로 세팅을 해주면  
이를 분석하여 자바 프로그램이 동작할 수 있게 된다.  
(스프링 프레임워크의 사용은 (초창기~현재)XML을 이용하는 방법이나 (본격적으로 스프링 4.0부터)자바 애노테이션을 이용하는 방법, 두 가지로 구분할 수 있다)

<U>프로젝트 관리가 용이하다.</U>

자바 파일에 직접 작업하는 게 아니라  
애노테이션이나 XML 파일로 작업해서  
관리를 하기 때문에 XML 파일을 열어보면  
전체 프로젝트가 어떻게 운영되고 있는지  
한 눈에 파악이 가능하기에 프로젝트 관리가  
용이하다.

<U>다수의 개발자와 동시에 프로젝트 개발하기 용이하다.</U>

<U>처음 프로젝트 세팅이 복잡하다.</U>

하지만 한번 프로젝트 세팅을 잘해놓으면  
이후의 작업은 굉장히 간결하고 쉽게  
개발이 가능하다.

<U>스프링 프레임워크에 대한 개념을 제대로 숙지하지 못하면 코드 분석조차 어렵다.</U>
 
스프링 프레임워크 동작원리 자체가  
구동에 필요한 정보를 기록해 놓으면  
스프링 프레임워크가 해닫 정보들을 가져다가  
개발자가 만든 애플리케이션을 구동시킨다.

따라서 개념과 동작원리를 잘 파악해야 한다. 

## IoC (제어의 역전)

프레임워크는 제어 흐름(시나리오)을  
이미 정의해 놓았다(=규정해 놓았다)  

이러한 logic의 흐름은 이미 정해져 있기에  
개발자가 직접 제어할 수는 없다.

개발자는 그저 중간중간에 자신이 구현하고 싶은 방향에  
클래스들을 구현하기에 편의성을 제공받음과 동시에  
코드의 견고함을 제고한다.  

ex. 디자인 패턴 中, 탬플릿 메서드



