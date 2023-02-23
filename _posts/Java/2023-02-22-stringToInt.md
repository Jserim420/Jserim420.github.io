---
title: "[Java][형변환] String to Int / Int to String"
categories:
    - Java
tag:
    - Java
    - 형변환
    - int
    - String
toc: true
toc_sticky: true
toc_label: "String ↔ Int"
---

# String ▶ Int
## ```Integer.parseInt()```
[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Integer.html)에 나와있는 ```parseInt()```은 아래와 같다.
- 클래스 : ```java.lang.Integer```
- 리턴 타입 : ```static int```
    - 타입이 static 이므로 인스턴스 객체를 생성하지 않고 바로 사용할 수 있다.
- 메소드 : ```parseInt(String s)```
- 설명 : 문자열 인수를 부호 있는 10진수 정수로 변환한다.

```java
String numStr = "16";
int num = Integer.parseInt(numStr);
```

paseInt()를 두번째 매개변수 없이 사용하면 자동으로 10진수 정수로 변환된다.

<br>

하지만, 두번째 매개변수를 사용하면 원하는 진법으로도 변환이 가능하다.
```java
String numStr = "16";
int num = Integer.parseInt(numStr, 16); // numStr을 16진법으로 변환
```

<br>

### ```java.lang.NumberFormatException```

그렇다면, String형 변수에 숫자가 아닌 값을 저장한 채 형변환을 하면 어떻게 될까?

```java
String numStr = "16A";
int num = Integer.parseInt(numStr);
```

<br>

![image](https://user-images.githubusercontent.com/81462623/220585409-04b243e9-6671-41c3-a070-f40dca544062.png)

이런 끔찍한 에러가 난다.

<br>

여기서 ```NumberFormatException``` 은 숫자 형식에 오류가 있다는 뜻이다.

문자열을 숫자로 바꾸는데 있어 문제가 발생했다는 것인데,

문자열에 숫자가 아닌 값이 포함되어 있기 때문에 유효하지 않는 값으로 예외가 발생했다는 것이다.

<br><br>

## ```Integer.valueOf()```
[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Integer.html)에 나와있는 ```valueOf()```은 아래와 같다.
- 클래스 : ```java.lang.Integer```
- 리턴 타입 : ```static Integer```
    - 타입이 static 이므로 인스턴스 객체를 생성하지 않고 바로 사용할 수 있다.
- 메소드 : ```valueOf​(String s)```
- 설명 : 지정된 String 값을 보유하는 Integer 객체를 반환한다.  

```java
String numStr = "30";
int num = Integer.valueOf(numStr);
```

```Integer.valueOf()```의 리턴값은 ```int```형이 아닌 ```Integer```객체 이다.

<br>

<b>int와 Integer의 차이는 무엇일까?</b>

```int```는 값이 저장될 공간의 크기와 저장 형식을 정의한 자료형 중 기본형이고,

```Integer```는 기본형을 객체로 다루기 위해 사용하는 래퍼 클래스이다.

<br>

이는 다음에 제대로 다뤄보기로 하고 ```valueOf()```의 리턴타입이 ```Integer``` 인것만 기억해두자.

<br><br>

## ```new Integer(Integer.parseInt())```
공식 문서를 보면 ```Integer.valueOf()```를 표현할 수 있는 또 다른 방법을 소개한다.
```
In other words, this method returns an Integer object equal to the value of:
    new Integer(Integer.parseInt(String s))
```

<br>

아래와 같이 사용할 수 있다는 것이다.

```java
String numStr = "60";
int num = new Integer(Integer.paseInt(numStr));
```

<br><br><br>

# Int ▶ String

## ```Integer.toString()```
[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Integer.html)에 나와있는 ```toString()```은 아래와 같다.
- 클래스 : ```java.lang.Integer```
- 리턴 타입 : ```static String```
    - 타입이 static 이므로 인스턴스 객체를 생성하지 않고 바로 사용할 수 있다.
- 메소드 : ```toString(int i)```
- 설명 : 지정된 정수를 나타내는 String 객체를 반환한다.

```java
int num = 814;
String numStr = Integer.toString(num);
```

<br>

문서를 보면, ```toString​(int i, int radix)``` 를 통해 변수를 원하는 진법으로도 변환이 가능하다.

```java
String numStr = Integer.toString(num, 16);
// num을 16진법으로 변환
```

<br><br>

## ```String.valueOf()```
[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html)에 나와있는 ```valueOf()```은 아래와 같다.
- 클래스 : ```java.lang.String```
- 리턴 타입 : ```static String```
    - 타입이 static 이므로 인스턴스 객체를 생성하지 않고 바로 사용할 수 있다.
- 메소드 : ```valueOf​(int i)```
- 설명 : char형 인수의 문자열 표현을 반환한다.

```java
int num = 63
String newStr = String.valueOf(num);
```

<br>

오라클 공식 문서를 살펴보면, ```valueOf()``` 메소드에 여러가지 매개변수가 존재한다. 

```boolean, 배열, double, float, char 등```

<br>

이는 ```int``` 뿐만 아니라 다른 타입도 ```String``` 타입으로 변환 할 수 있음을 뜻한다.