---
title:  "[Design Pattern] 싱글턴 패턴(Singleton Pattern)"
excerpt: "자바를 통해 디자인 패턴 중, 싱글턴 패턴에 대한 이해"

categories:
  - Design Pattern
tags:
  - 디자인 패턴
last_modified_at: 2020. 9. 18. 23:42
---

## Singleton(싱글턴, 단일체)  

인스턴스를 오직 하나만 생성할 수 있는 클래스  
(단 하나만 존재하는 인스턴스 ex. 대한민국 기준 날짜)

즉, 오직 한 개의 인스턴스만을 갖도록 '보장'하고,  
이에 대한 '전역적인(global)' 접근점을 제공한다.

<br/>

- 생성자는 private으로

- static으로 유일한 객체 생성

- 외부에서 유일한 객체를 참조할 수 있는 "public static get()" 메서드 구현

<br/>

```java
public class Member {

    static {
        System.out.println("싱글턴 패턴 성공");
    }

    private static final Member memberInstance = new Member();

    private Member() {
        System.out.println("인스턴스화 성공");
    }

    public static Member getInstance() {
        /*
        if (memberInstance == null) {
            memberInstance = new Member();
        }
        */
        return memberInstance;
    }

}
```

```java
class MemberTest {
    public static void main(String[] args) {
        Member member1 = Member.getInstance();
        Member member2 = Member.getInstance();

        System.out.println(member1);
        System.out.println(member2);
    }
}
```

![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Java__SingletonPattern/1.png?raw=true)


싱글턴 패턴은 디자인 패턴 중, 하나의 패턴이다.  
그리고 디자인 패턴은 객체지향 설계자들이  
매일 부딪치게 되는 많은 문제를 다양한 방법으로 해결해 준다.

Java는 객체지향 언어이다.  
일반적으로 JavaScript의 전역(global) 개념과 달리  
모든 변수와 메서드는 클래스 내부에 종속돼 있다.

이러한 특징은 장점으로써 Java의 견고함(안정성)을 제고한다.

클래스 자신이 자기의 유일한 인스턴스로 접근하는 방법은  
해당 클래스의 인스턴스가 유일함을 보장하고,  
또 다른 인스턴스 생성을 미연에 방지하는데  

이를 싱글턴 패턴(Singleton Pattern)이라 한다.

<br/>

싱글턴 패턴은 다음과 같은 상황에서 사용한다.

- 클래스의 인스턴스가 오직 하나여야 함을 보장하고,  
잘 정의된 접근점(access point)으로 모든 사용자가 접근할 수 있도록 해야 할 때


- 유일한 인스턴스가 서브클래싱(클래스 상속)으로 확장돼야 하며,  
사용자는 코드의 수정없이 확장된 서브클래스의 인스턴스를 사용할 수 있어야 할 때

<br/>

싱글턴을 만드는 방식은 2가지다.

두 가지 방식 모두 생성자를 private으로 감춰두고,  
유일한 인스턴스에 접근할 수 있는 수단으로  
public static 멤버(변수 or 메소드)를 '하나' 마련해둔다.

<br/>
<br/>

*참고자료

<U>이펙티브 자바 3/E - 조슈아 블로크 지음</U>

<U>GoF의 디자인 패턴 개정판 - 에릭 감마, 리처드 헬름, 랄프 존슨, 존 블리시디스 지음</U>
