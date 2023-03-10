---
title: "[Java][형변환] String to Array / Array to String"
categories:
    - Java
tag:
    - Java
    - 형변환
    - String
    - Array
toc: true
toc_sticky: true
toc_label: "String ↔ Array"
---

# String ▶ Array

## split()
```split()``` 함수는 ```java.lang.String``` 클래스에 있는 함수이다.

[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html)에 나와있는 ```split()```은 아래와 같다.
- 클래스 : ```java.lang.String```
- 리턴 타입 : ```String[]```
- 메소드 : ```split​(String regex)```
- 설명 : 지정된 정규 표현식의 일치 항목을 기준으로 문자열을 분할한다.

```java
String name = "Hello Java";
String[] nameArr = name.split("");
```

공백을 포함한 name 의 값이 ""를 기준으로 분할되어 nameArr에 저장된다.

```nameArr[] = {"H", "e", "l", "l", "o", " ", "J", "A", "V", "A"}```이다.

공식문서를 보면 분할 할 수 있는 개수를 정할 수 있는 것을 알 수 있다.

<br>

### ```split(String regex, int limit)```
limit개의 배열로 저장된다.

```java
String num = "010-123-456-789";
String[] numArr = num.split("-", 3);
```

"-" 를 기준으로 3개의 배열로 나누면

```nameArr[] = {"010" , "123", 456-789"}``` 이다.

<br><br>

# Array ▶ String

## ```Arrays.toString()```
[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Arrays.html)에 나와있는 ```toString()```은 아래와 같다.
- 클래스 : ```java.util.Arrays```
- 리턴 타입 : ```String```
- 메소드 : ```toString(Object[] a)```
- 설명 : 지정된 배열의 내용을 나타내는 문자열을 반환한다.

```java
String[] name = {"경기", "서울", "부산", "제주"};
String nameStr = Arrays.toString(name);
```

nameStr을 출력해보면 결과는 아래와 같이 출력된다.

```
[경기, 서울, 부산, 제주]
```

toString()은 String으로 출력하고자 하는 배열의 값을 ```[값1, 값2, 값3, ···]```의 형태로 출력하기 때문에, 네개의 값을 모두 이어 ```값1값2값3···``` 로는 출력할 수 없다.

<br>

## ```String.join()```
[오라클 공식 문서](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html)에 나와있는 ```join()```은 아래와 같다.
- 클래스 : ```java.lang.String```
- 리턴 타입 : ```static String```
    - 타입이 static 이므로 인스턴스 객체를 생성하지 않고 바로 사용할 수 있다.
- 메소드 : ```join​(CharSequence delimiter, CharSequence... elements)```
- 설명 : 지정된 delimiter 배열의 복사본과 결합된 elements의 복사본으로 구성된 새 문자열을 반환한다.

```java
String[] name = {"경기", "서울", "부산", "제주"};
String nameStr = String.join(name, "");
```

name 배열의 값을 ""로 연결하여 nameStr에 저장한다는 뜻이다.

nameStr을 출력해보면 nameStr = ```경기서울부산제주``` 로 출력된다.

<br>

원하면 ```join(name, " 그리고 ")``` 을 통해 다른 형태의 값으로 출력할 수 있다.

```join(name, " 그리고 ")```을 사용하면 nameStr = ```경기 그리고 서울 그리고 부산 그리고 제주``` 로 출력된다.

<br><br>

# String ▶ char[]
지금까지는 문자열을 문자열 배열로 바꾸는 방법을 알아보았다.

이제는 문자열을 하나하나 쪼개 char형 배열로 바꾸는 방법을 알아보자.

<br>

## toCharArray()
```toCharArray()``` 함수는 ```java.lang.String``` 클래스에 있는 함수이며, 원하는 문자열을 char[] 형 문자 배열로 반환한다.

```java
String name = "Hello";
char[] charName = name.toCharArray();
```

위에서 charName[] 은

```charName[] = {'H', 'e', 'l' , 'l', 'o'}``` 으로 반환된다.

<br>

split() 과 다른 점은 배열을 나누는 기준을 정할 수 없어 위처럼 char형의 값으로 하나씩 쪼개져 배열로 반환된다는 것이다. 

<br><br>

# char[] ▶ String
char형 배열을 String으로 변환할 수도 있다.

문자열을 분할하여 조건에 맞게 정렬하고, 정렬한 배열을 다시 문자열로 변환할 때 사용할 수 있다.

<br>

## String 생성자

```java.util.String``` 클래스의 생성자 중 ```String(char[] value)``` 를 통해 char 배열을 문자열로 변환할 수 있다.

생성자를 사용해 객체를 생성하면 된다.

```java
char[] city = {'L', 'O', 'V', 'E'};
String cityName = new String(city);
````

위 결과 ```cityName = LOVE``` 가 된다.