---
title: "[Java][형변환] Char to String / String to Char"
categories:
    - Java
tag:
    - Java
    - 형변환
    - String
    - char
toc: true
toc_sticky: true
toc_label: "Char ↔ String"
---

# Char ▶ String

## ```String.valueOf()```
[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html)에 나와있는 ```valueOf()```은 아래와 같다.
- 클래스 : ```java.lang.String```
- 리턴 타입 : ```static String```
    - 타입이 static 이므로 인스턴스 객체를 생성하지 않고 바로 사용할 수 있다.
- 메소드 : ```valueOf​(char c)```
- 설명 : char형 인수의 문자열 표현을 반환한다.

```java
char newChar = 'A';
String newStr = String.valueOf(newChar);
```

<br>

오라클 공식 문서를 살펴보면, ```valueOf()``` 메소드에 여러가지 매개변수가 존재한다. 

```boolean, 배열, double, float, int 등```

<br>

이는 ```char``` 뿐만 아니라 다른 타입도 ```String``` 타입으로 변환 할 수 있음을 뜻한다.

<br><br>

# String ▶ Char
## ```charAt()```
[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html)에 나와있는 ```charAt()```은 아래와 같다.
- 클래스 : ```java.lang.String```
- 리턴 타입 : ```char```
- 메소드 : ```charAt(int index)```
- 설명 : 지정된 인덱스의 값을 반환한다.

```java
String newStr = "Hello Java";
char newChar = newStr.charAt(1);
```

```newStr```의 1번째 인덱스를 반환하겠다는 의미이다.

위와 같이 사용하면 ```newChar```는 'e'이다.

<br>

## ```toCharArray()```
- 클래스 : ```java.lang.String```
- 리턴 타입 : ```char[]```
- 메소드 : ```toCharArray()```
- 설명 : 문자열을 새로운 문자 배열로 변환한다.

```java
String newStr = "Hello";
char[] charArr = newStr.toCharArray();
```

```newStr```의 문자열을 새로운 문자 배열로 반환한다.

```charArr```는 size가 5개인 char 배열이 되는 것이다.

<br>

```for문```을 이용하면 ```charArr 배열``` 의 값을 확인할 수 있다.

```java
for(char c : charArr) {
    System.out.println(c);
}
```

주의할 점은 특수문자나 공백도 인덱스에 포함된다.
