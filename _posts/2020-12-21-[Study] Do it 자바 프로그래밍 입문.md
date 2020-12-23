---
title: "[Study] Do it 자바프로그래밍 입문"
categories:
    - dev
tags:
    - dev
    - java
toc: true
---

## 1장 자바 프로그래밍 시작하기

* Java SE 1.8 설치
* 이클립스 설치

* 패키지 : 폴더 개념
* Entry Point : 시작점 :: static void main()
* print 함수 ::  System.out.println();
* () : 연산자 = 함수호출할 때 그곳으로 가라는 뜻, () 앞은 주소
  () : 연산자 = 계산식에서는 우선순위 부여
* 문자열 " " 사용
* ctrl+/ :: 주석처리
* 코드창의 글자 크기 설정 :: window>preference>General>Appearance>Colors and Fonts>Basic>Text Font>Edit 

	/*  */ 주석처리
	/** 해서 엔터를 치면 javadoc이 실행됨 : 설명문 달기
	
> src 폴더에서 .java 실행을 하면 bin 폴더에 .class 바이트 코드가 생성됨

```java
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println("안녕 자바 \n");
	}
```

> public :: 공개, 오픈되어 있음 
> static :: 정적
> void :: 리턴값이 없음
> 자바는 무조건 클래스가 있어야 함. 모든게 클래스 안에 있어야함. 또 클래스 안에 메서드가 있어야 함.
> first class : 클래스가 가장 높음 
> 클래스 밖에 코드를 쓰면 안됨
> main()은 하나 이상 있어야 실행이 됨. :: runable class
> main()이 없으면 :: 순수클래스, 실행이 안됨

# 2장 변수와 자료형

변수의 선언과 함께 초기화를 해 준다.
선언 후 곧바로 호출(사용) 시 에러가 뜨도록 되어 있음

덧셈을 할 경우 초기화 값은 0
곱셈을 할 경우 초기화 값은 1
문자열 초기화 ""


> 컴파일 타임 상수

```Java
	final int MAX_NUM = 100;
```

> 런타임 상수

```Java
	final int ADD_NUM = add();
```

* 문자 타입 char (2바이트) 
* 정수 타입 int (4바이트) 기본형
* 실수 타입 double (8바이트) 기본형
* long을 넘어가면 숫자는 문자열로 받아서 처리한다.
* 런타임 환경에서 에러 나는 것보다 컴파일 에러가 훨씬 나음.



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM4ODA1MTQwMCwxMzQzNDgyMTk3LDExOD
E4NDAzMzEsOTUwNDExMzU3LDE3Mzc5Njg3ODksMTQ3OTYwMjUz
LDU2ODIyMjI3NiwtODc1NDkwOTM3LDI3NjI1MzYxLC0xMjY4ND
gzODg1LDE2NzQ2Mzc4NTksMTA0OTE2MTg5NSwtMTQzMTY3OTcy
M119
-->