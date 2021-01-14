---
title:  "[Java] 람다식 "
excerpt: "자바 람다식에 대한 개념과 예제"
toc: true
categories:
  - Java
tags:
  - 람다식
  - 자바
last_modified_at: 2020. 5. 30. 10:08
---

## Java

Java는 객체지향 프로그래밍(OOP) 언어다.  
따라서 객체가 없이 메소드를 호출하는 등의 기능은 쉽지 않다.

하지만 Java 8부터 ' 함수형 프로그래밍 '도 지원하기 시작하면서  
내부적으로 익명 객체가 생성되는 등 Java 언어의 기능이 확장되었다.  
즉, 이제 Java는 객체지향언어인 동시에 함수형 언어가 되었다

<br/>

## Java Lambda Expression(람다식)

자바에서 함수형 프로그래밍을 구현하는 방식

메서드를 하나의 '식'으로 표현한 것.

ex. (x,y) -> x + y에서 x + y에는 세미콜론(;)이 없다(하나의 '식'으로 표현되었기 때문)

<br/>

람다식은 함수를  

- <U>간략하면서도</U>(코드량 감소)  

- <U>명확한</U>(@FunctionalInterface를 통해 해당 함수형 인터페이스 내부에  
단 하나의 추상 메소드만을 사용했다는 의사를 람다식 코드를 통해 쉽게 확인 가능)

'식(expression)'으로 표현할 수 있게 해준다.

<br/>

※ '식(expression)'과 문장(statement)를 반드시 구분하자.  

'식(expression) ex. 1 + 2  
문장(statement) ex. 1 + 2;

<br/>

### 람다식 특징)

- '매개 변수'와 '추상 메서드(함수)의 재정의한 구현(implement)'만으로 기능을 수행

- 메서드 매개변수, 리턴 타입, 그리고 ※변수로 만들어 사용할 수 있다(※ 메서드를 변수처럼 다루는 것이 가능해진다)

```java
//    변수      ---------구현부--------
int largerInt = (x, y) -> x > y ? x: y;
```

<br/>

- 함수형 인터페이스(@FunctionalInterface)의 '인스턴스'를 만드는 방식으로 사용할 수 있다.  
*FunctionalInterface :  추상(abstract) 메소드를 단 하나만 가지고 있는 인터페이스

당연하게도 인터페이스 내부에 (추상) 메소드가 여러 개라면  
람다식으로 변형된 코드의 의미를 알기 힘들기 때문. 

------------------------------------------------

↓reason
 
![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Java__lambda/1.png?raw=true)

이렇게 함수형 인터페이스 내부에 추상 메서드가 하나가 아니라면,  
단순히 해당 인터페이스 외부에서 사용한 람다식 "(v1, v2) -> {}" 코드만 보고서

어느 추상 메서드를 재정의한 지 파악하는 건 불가능하다.

![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Java__lambda/2.png?raw=true)

삼항 연산자도 사용할 수 없는 관계로 불가피하게 길어진 코드...

![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Java__lambda/3.png?raw=true)

![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Java__lambda/4.png?raw=true)

이런 호출은 애초에 함수형 인터페이스가 아닌 일반 인터페이스를 사용하는 것이다.

-----------------------------------------------------------------------------

※ 단, Java 8부터  static 메소드나 default 메소드는 함수형 인터페이스 내부임에도 불구하고  
함수형 인터페이스 내 일반적인 추상 메서드와 달리 갯수에 제약이 없다.

<br>

4. 내부적으로 '익명 객체'(익명 (내부) 클래스)가 생성된다(외부에선 보이지 X)  
->  문법이 Simple해지는 효과(코드를 줄일 수 있다)  
    
람다식은 사실 익명 (내부) 클래스의 객체와 동등하다.

함수형 인터페이스를 구현한 '익명 객체'(익명 (내부) 클래스)를  
람다식으로 대체하는 이유는 사실 람다식이 실제로는 익명 객체이며,

익명 객체 내부의 기존 추상 메서드를 재정의한 메서드와 람다식의 매개변수의 타입과 갯수 그리고 반환값이 일치하기 때문.

<br/>
<br/>

### ※ 함수형 프로그래밍  

순수 함수(pure function)를 구현하고 호출

매개변수를 받아서 프로그래밍을 하게 되면 '외부 변수'들을 사용하지 않음 ( = 순수 함수형 프로그래밍)

-> 외부 데이터(자료)에 Side Effect가 발생하지 않도록 함(부수적인 영향을 주지 X = 함수 밖(외부)의 값을 변경하지 못함)

----------------------------------------

↓reason

-> 메서드(함수)를 호출하면 지역 변수 등의 'Stack'이 쌓이게 되고 메서드가 종료하면 LIFO에 따라 스택이 없어진다.  
이는 Call by Value로써 메서드 외부에 있는 변수 등에 영향을 미치지 못한다.  

즉, 메서드 외부의 값을 변경하지 못한다.(※ Java Call by Value vs Call by Reference 참조할 것)

여담으로, Garbage Collector는 Heap 영역만 치운다.

-------------------------------------------------

(ex. 이 함수가 돌아감으로써(입력 받은 자료를 기반으로 수행되고)  
외부에 영향을 미치지 않으므로 다른 변수값들이 변하지 않기에  
'병렬 처리'가 가능하는 등의 '안정적'이고 '확장성'있는 프로그래밍 방식) 

<br/>

### Java에서 함수형 프로그래밍

- 함수를 첫 번째 클래스 객체로 사용할 수 있다.

- Side Effect가 없다(함수 밖의 값을 변경하지 못함)

- 함수 밖(외부)에 정의되어 있는 '상태'가 없다.

- 함수가 함수를 '매개변수'로 받을 수 있고 '리턴'할 수도 있다.

<br/>

### Q. 메서드와 함수의 차이가 뭐죠?

A. 전통적으로 프로그래밍에서 함수라는 이름은 수학에서 따온 것입니다.
   
수학의 함수와 개념이 유사하기 때문이죠.  
그러나 객체지향 개념에서는 함수(function) 대신  
객체의 행위나 동작을 의미하는 메서드(method)라는 용어를 사용합니다.

메서드는 함수와 같은 의미이지만, 특정 클래스에서 반드시 속해야 한다는 제약이 있기에  
기존의 함수와 같은 의미의 다른 용어를 선택해서 사용한 것입니다.
  
그러나 이제 Java 8 이후로 람다식을 통해서는 메서드가 다시 하나의 독립적인 기능을 하기에  
함수라는 용어를 사용하게 되었습니다.

[<U>참고자료: Java의 정석 제 3판, 남궁성 저 (클릭)</U>](http://www.kyobobook.co.kr/product/detailViewKor.laf?ejkGb=KOR&mallGb=KOR&barcode=9788994492032&orderClick=LAG&Kc=)

<br/>
<br/>

### 람다식 문법)

- 매개 변수가 하나인 경우, 괄호 생략 가능(but 두 개인 경우, 생략 불가능)

```java
str -> {System.out.println(str);}
```

매개 변수가 하나이기 때문에 (str)이 아닌 괄호를 생략한 str으로 표현
매개 변수에 자료형 생략 가능

<br/>

- 중괄호( {, } ) 안의 '구현부'가 한 문장인 경우, 중괄호 역시 생략 가능

```java
str -> System.out.println(str);
```

<br/>

- 중괄호 안의 구현부가 반환문 하나라면, return과 중괄호를 모두 생략 가능

```java
(x,y) -> x + y  // (x,y) -> {return x + y;} 
//두 값을 더하여 반환


str -> str.length() // str -> {return str.length();} 
//문자열 길이를 반환
```

위의 코드를 살펴보면

```java
(x,y) -> x + y
```

마무리에 세미콜론(;) 표시가 없다.  
이는 문장(statement)이 아닌 '식(expression)'이므로 끝에 ;를 붙이지 않는다.

<br/>
<br/>

먼저 함수형 인터페이스를 선언하자.

```java
package lambda1;

@FunctionalInterface
public interface RunLambda {
    void doLambda();
}
```

```java
package lambda1;

public class Foo {
    public static void main(String[] args) {
        //익명 내부 클래스(anonymous inner class)
        RunLambda runLambda = new RunLambda() {
            @Override 
            public void doLambda() { 
                System.out.println("Hello, Lambda!"); 
            }
        };
    }
}
```

![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Java__lambda/5.png?raw=true)

인텔리J 기능을 활용하면 기존의 '익명 내부 클래스' 방식을 '람다 식'으로 변경할 수 있다

![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Java__lambda/6.png?raw=true)

<br/>

※주의

```java
package lambda1;

public class Foo {
    public static void main(String[] args) {
        //익명 내부 클래스(anonymous inner class)
        RunLambda runLambda = new RunLambda() {
            @Override 
            public void doLambda() {
               /*
               재정의할 메소드 내부에 여러 코드가 혼재할 경우,
               람다식으로 깔끔하게 코드를 변형하지 못한다
               */
                System.out.println("Hello, Lambda!");
                System.out.println("Hello, Lambda!");
                System.out.println("Hello, Lambda!");
                System.out.println("Hello, Lambda!");
                System.out.println("Hello, Lambda!");
            }
        };
    }
}
```

'람다식'을 실행하는 메소드는 기존의 '익명 내부 클래스(anonymous inner class)'의 실행 방식과 동일하게 호출 가능하다

```java
runLambda.doLambda(); // 결과값 : Hello, Lambda!
```

※ 오답 노트 :  

람다식에서 자주 실수하는 점이 이 부분이다.  

기존의 익명 내부 클래스를 보면 알 수 있듯,  
인터페이스 내 추상 메소드를 재정의(Override)했을 뿐이기에  
정작 프로그램을 실행하더라도 당연히 아무런 일도 발생하지 않는다.

인스턴스를 통해 재정의한 메소드를 호출하자.  

<br/>
<br/>

### 람다식의 다른 사용 방법 like JavaScript's functional programming

```java
@FunctionalInterface
public interface LambdaInterface {

    void showString(String v1);

}

public class LambdaInterfaceImpl {
    public static void main(String[] args) {
        LambdaInterface lambdaVar1 = s -> System.out.println(s);
        showThisString(lambdaVar1);
    }

    private static final void showThisString(LambdaInterface l) {
        l.showString("This String");
    }
}
```

```java
@FunctionalInterface
public interface LambdaInterface {

    void showString(String v1);

}

public class LambdaInterfaceImpl {
    public static void main(String[] args) {
        LambdaInterface lambdaVar2 = returnString();
        lambdaVar2.showString("This String");
    }
    
    private static final LambdaInterface returnString() {
        return s -> System.out.println(s + " plus String!!!");
    }
}
```

<br/>

```java
@FunctionalInterface
public interface LambdaInterface {

    void showString(String v1);

}

public class LambdaInterfaceImpl {
    public static void main(String[] args) {
        LambdaInterface lambdaVar1 = s -> System.out.println(s);
        showThisString(lambdaVar1);

        LambdaInterface lambdaVar2 = returnString();
        lambdaVar2.showString("This String");
    }

    private static final void showThisString(LambdaInterface l) {
        l.showString("This String");
    }

    private static final LambdaInterface returnString() {
        return s -> System.out.println(s + " plus String!!!");
    }
}
```

![](https://github.com/gyumeen/blog-images/blob/main/2021/01/Java__lambda/7.png?raw=true)

빠른 예제 작성을 위해 부득이하게도  
main 메서드 내부에서 람다 관련 메서드를 즉각 호출하기 위해  
동일 클래스 내부이면서 main 메서드 외부에 static 메서드를 만들었지만

사실 이러한 프로그래밍은 엄밀히 따져서 객체지향 원칙에 위배된다.

<br/>

### 기타 람다식 예제

```java
import java.util.Scanner;

@FunctionalInterface
interface Add {
    void addNumber(int a, int b);
}

public class IntegerAB {

    static void makeScanner(Scanner scanner) {

        while (true) {

            System.out.println("1 이상 9 이하의 수로 입력한 두 수를 더합니다.");

            int a = scanner.nextInt();
            int b = scanner.nextInt();

            if (a > 0 && b < 10) {
                Add add = (a1, b1) -> System.out.println(a1 + b1);
                add.addNumber(a,b);

                scanner.close();
                break;
            }
        }
    }

    public static void main(String[] args) {

        IntegerAB.makeScanner(new Scanner(System.in));

    }
}
```



