---
title: "[JavaScrpit] 자바스크립트 기본 문법"
categories:
    - JavaScript
tag:
    - JavaScript
    - 기본 문법
toc: true
toc_sticky: true
toc_label: "JavaScript"
---

# 로그 띄우기 (출력)
```javascript
console.log("HelloWorld")
```

<br>

# 변수 선언
자바스크립트는 Java, C와 다르게 자료형 없이 변수 선언이 가능하다.
```javascript
var 변수명 = 값

var a = 1
a = "안녕하세요" // a는 문자
```

a 라는 같은 변수에 다른 자료형을 넣으면 자동으로 자료형이 변경되어 저장된다.

<br><br>

# 배열 선언
자바스크립트 배열은 []를 이용한다.
```javascript
var 배열명 = [값1, 값2, 값3, ···]

var arrayList = ["사과", "딸기", "배"]

```

<br>

## 배열 출력
```javascript
console.log(arrayList) // arrayList 전체 출력
console.log(arrayList[0]) // arrayList의 0번째 인덱스 출력
```

```console.log(arrayList)```는 arrayList 배열의 전체가 ```["사과", "딸기", "배"]``` 로 출력된다. 

<br>

## 배열에 값 추가
```javascript
arrayList.push("바나나")
```

위와 같이 "바나나" 값을 추가하면, ```arrayList``` 맨 뒤에 "바나나" 값이 추가 된다.

<br><br>

# 함수 선언
```javascript
function 함수명() {
    변수 : 값
}
```

```javascript
function test() {
    console.log("함수생성")
}

test() // test함수 실행
```

<br>

## 함수를 변수로 선언하기
기본형 뿐만 아니라 함수도 변수로 선언하여 저장할 수 있다.

```javasript
var test1 = function() {

}
```

<br><br>

# 오브젝트 생성
자바스크립트는 클래스를 따로 생성하지 않고 선언한다.
```javascript
var 오브젝트명 = {
    변수 : 값
}
```

자바스크립트 오브젝트에서의 필드는 ```변수:값``` 의 형태로 선언한다.

```javascript
var person = {
    name : "JavaScript",
    age : "10"
}

console.log(person.name)
console.log(person.age)
```

<br>

## 함수 생성
오브젝트 필드에서 함수도 생성할 수 있다.

함수 생성에는 3가지 방법이 있다.

```
1. 함수명 : function() { }
2. 함수명() { }
3. 함수명 : () => { }
```

<br>

위의 세가지 방법을 이용해 필드 내 함수를 생성해보자.

```javascript
var person = {
    name : "JavaScript",
    age : "10",
    intro : function () {
        console.log("안녕하세요. " + this.name + "입니다.")
    },

    intro2() {
        console.log("안녕하세요. " + this.age + "살 입니다.")
    },

    intro3 : () => {
        console.log("안녕하세요." + this.name + "입니다.")
    }
}

person.intro()
person.intro2()
person.intro3()
```

직접 출력해보면, ```greeting()``` 에서 가르키는 ```this.name```은 오브젝트내 name필드의 값을 의미하며, ```greeting2()``` 의 ```this.age``` 는 오브젝트내 age필드 값을 의미한다는 것을 알 수 있다.

<br>

하지만, ```person.intro3()```의 ```this.name``` 은 ```undefined```로 출력될 것이다. 그 이유는 람다값을 사용할 때 this가 가르키는 값은 해당 필드가 아닌, 오브젝트 전체(person)이기 때문이다. 

<br>

그렇기 때문에 람다식을 사용하는 경우, 아래와 같이 this필드의 값을 초기화 해주어야 한다.

```javascript
var person = {
    name : "JavaScript",
    age : "10",
    this.name : "JavaScript",
    intro3 : () => {
        console.log("안녕하세요." + this.name + "입니다.")
    }
}
```