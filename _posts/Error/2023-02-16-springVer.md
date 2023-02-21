---
title: "[Spring-Boot] java error: release version 17 not supported"
categories:
    - Error
tag:
    - 스프링부트
    - 자바
    - 자바 버전
toc: true
toc_sticky: true
toc_label: "버전 오류"
---

# java error: release version 17 not supported
스프링부트 처음 프로젝트 생성하고 실행하려는데 자바 17 버전 오류가 뜨길래 너무 당황했다...
<br>
![Error](https://user-images.githubusercontent.com/81462623/219638251-ffe4426d-3453-4cfb-9fea-6da050cc1663.png)
<br>
네? 갑자기 무슨소리세요? 
<br>
Java17 사용할 생각도 없었고 Java11 사용하고 있어서 갑자기 멘붕옴


<br><br><br>

## 원인
나는 Java11를 쓴다. 그리고 스프링 부트 스타터로 프로젝트를 생성했다.
<br>
놀랍게도 스프링 부트 스타터로 프로젝트를 생성할때 Java 버전을 17로 설정했다.
<br><br>
왜?.. 대체 왜..?

<br>
스프링부트 3.0으로 프로젝트를 생성했는데, 3.0 부터는 Java17이상을 사용해야 하고 그러다보니 자동으로 Java17이 선택되었네요..

<br><br>

## 해결방법

### JDK17 설치
제일 간단한 방법

<br>

Download 🔽
<br>
[다운로드 링크](https://www.oracle.com/java/technologies/downloads/)

<br><br>

### IntelliJ 설정 변경
난 이걸로 해결했다.
<br>
왜냐면 그냥 다운받으면 또 기다려야하니까..

1. File -> Settings -> Compiler -> Java Compiler : 11
2. File -> ProjectStructure -> Language level : 11
