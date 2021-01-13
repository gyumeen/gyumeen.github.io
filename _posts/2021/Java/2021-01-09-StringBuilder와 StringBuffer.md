---
title: "[Java] StringBuilder와 StringBuffer"
excerpt: "멀티 쓰레드 프로그래밍에서 동기화 보장의 차이 - StringBuilder만 동기화 보장"

categories: 
  - Java
tags: 
  - 자바 문법
  - 멀티쓰레드
  - 동기화
last_modified_at: 2020. 10. 2. 05:18
---

## StringBuilder vs StringBuffer  
가변적인(String은 대표적인 불변 클래스) char[] 배열을 멤버변수로 가지고 있는 클래스들

<br/>

``` java
public class BuilderBuffer {
    public static void main(String[] args) {
        String hello = "Hello, ";
        //String world = "World!";

        StringBuilder stringBuilder = new StringBuilder(hello);
        stringBuilder.append("World!");
        //stringBuilder.append(world);

        String result = stringBuilder.toString();
        System.out.println(result);
    }
}
```
<br/>

StringBuilder는 멀티 쓰레드 프로그래밍에서 동기화(synchronization)가 보장됨.  
반면, StringBuffer는 동기화가 보장 X.

멀티 쓰레드 환경일 경우,  StringBuilder를 사용하고  
아닐 경우,  StringBuffer를 사용.

<br/>

toString 메서드를 통해 String 타입으로 반환 필요.

``` java
String result = stringBuilder.toString();
```
