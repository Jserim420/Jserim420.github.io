---
title: "[Java][형변환] Int to Char / Char to Int"
categories:
    - Java
tag:
    - Java
    - 형변환
    - int
    - char
toc: true
toc_sticky: true
toc_label: "Int ↔ Char"
---

# Int ▶ Char
## ```(char)```
타입 캐스팅을 이용해 ```int```를 ```char```로 변환할 수 있다.

<br>

### ASCII
```java
int num = 65;
char numChar = (char) num;
```

하지만 위와 같이 변환하면 ```numChar```는 65의 아스키코드값인 'A'가 된다.

이렇게 ```(char)```만을 사용하면 ASCII 값으로 표현되기 때문에 주의해야 한다.

<br>

### 0~9
ASCII 값이 아닌 ```char```로 변환하기 위해서는 숫자에 작은따옴표 ```''``` 만 붙여주면 된다.

```java
int num = '1'
char numChar = (char) num;
```

<br>

이외에도 문자 '0'을 더해주는 방법도 있다.


```java
int num = 3;
char numChar = (char)(num+'0');
```

그렇다면 왜 '0' 일까?

아래의 아스키코드표를 살펴보자.

![ASCII](https://blog.kakaocdn.net/dn/qOPNt/btrAdcY26CF/Ksn1qKzUqEaCql1Cbk6GG0/img.png)

위의 표를 보면 char'0'의 10진수는 80이다.

각 숫자에 80을 더해 아스키코드표의 '0'~'9'를 찾는 것이다.


<br><br>

## ```Character.forDigit​()```

[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Character.html)에 나와있는 ```forDigit()```은 아래와 같다.
- 클래스 : ```java.lang.Character```
- 리턴 타입 : ```static char```
    - 타입이 static 이므로 인스턴스 객체를 생성하지 않고 바로 사용할 수 있다.
- 메소드 : ```forDigit(int digit, int radix)```
- 설명 : 지정된 기수의 특정 숫자에 대한 문자 표현을 결정한다.

<br>

즉, ```int``` 형 숫자를 원하는 진법으로 변환한다는 뜻이다.
```java
int num = 9;
char numChar = Character.forDigit(num, 10); // 9를 10진법으로 변환
```

<br>

16진법으로 변환하고 싶다면 다음과 같이 표현한다.
```java
int num = 12;
char numChar = Character.forDigit(num, 16); // 12를 16진법으로 변환
```

<br><br>

## ```toString()```
여기서 ```toString()```은 ```Integer 클래스```의 메소드를 말한다.

```int```형 숫자를 ```String```으로 변환한 후, 변환한 ```String```의 ```char``` 값을 가져 오는것이다.

그렇기 때문에, ```toString()```만을 사용하여 ```int```를 ```char```로 변환할 수는 없다.

<br>

말로 표현하는 것보다 코드로 보면 더 쉽다.

```java
int num=1;
char numChar = Integer.toString(num).charAt(0);
```

여기서 ```charAt(0)```은 ```num```을 ```string```으로 변환한 "1"의 0번째 인덱스를 말한다.


<br><br><br>

# Char ▶ Int
## Character.getNumericValue()
[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Character.html)에 나와있는 ```getNumericValue()```은 아래와 같다.
- 클래스 : ```java.lang.Character```
- 리턴 타입 : ```static int```
    - 타입이 static 이므로 인스턴스 객체를 생성하지 않고 바로 사용할 수 있다.
- 메소드 : ```getNumericValue​(char ch)```
- 설명 : 지정된 유니코드 문자가 나타내는 int 값을 반환한다.

```java
char newChar = '3';
int newInt = Character.getNumericValue(newChar);
```

<br>

## '0' 빼기
위에서 설명한 Int to Char 형변환과 같은 원리이다.

```java
char newChar = 'A'
int newInt = newChar - '0'
```
 
위를 실행하면 newInt는 'A'의 10진수 97에 '0'의 10진수 80을 뺀 17이 된다.

그러므로 char형을 변환할때 변수 값에 숫자가 아닌 값을 저장해도 형변환 오류인 ```NumberFormatException``` 예외는 발생하지 않는다.