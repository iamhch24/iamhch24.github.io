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
* 연산자(리턴값 있음, 순위중요) -> 표현식 vs 선언식
* 과거 값을 사용하고 싶을 때
num = num +1 :: 자기 자신이 들어가야 함
* shift 연산자 :: 비트수를 움직임

> 한글입력

```Java
public static void main(String[] args) throws Exception {
	byte[] str_buffer = new byte[1024];
	int value2 = System.in.read(str_buffer);
	String str = new String(str_buffer);
	System.out.println(str);
}
```
>크리스마스 트리
```Java
package loopeaxample;

public class ChristmasTree {

	public static void main(String[] args) throws Exception {
		// TODO Auto-generated method stub
		String star ="*";
		String line ="";
		for(int i= 1;i<=5;i++) {
			line ="";
			for(int j=0;j<=5-i;j++) {
				line += "  ";
			}
			System.out.println(line+star+line);
			star += " * *";
			
		}
		for(int z= 1;z<=3;z++) {
			System.out.println("         | |");
		}	
	}
}

```

# 5장 클래스와 객체

new 연사자는 heap에 메모리 할당해 줌
지역 변수는 stack에 메모리 생김
전역 변수, static 변수는 data 영역에 메모리 생김

* main() 함수를 포함한 실행 클래스를 따로 만든다

* public get/set 메서드를 사용하여 캡슐화 함.

>접근제어자
public : 외부 클래스 어디에서나 접근 가능
protected : 상속한 경우, 같은 패키지 내부에서만 접근 가능
없는 경우 : default, 같은 패키지 내부에서만 접근 가능
private : 같은 클래스 내부에서만 접근 가능

# 6장 클래스와 객체 2
* this : 자신의 메모리를 가리키는 this 

* static 변수 : 클래스에서 공통으로 사용하는 변수를 'static'변수로 선언함. static 변수는 프로그램이 실행되어 메모리에 올라갔을 때 딱 한번 메모리 공간이 할당되고 그 값은 모든 인스턴스가 공유함. 클래스에 기반한 변수라고 해서 클래스 변수라고도 함.

* 클래스 메서드 : static 변수를 위한 메서드

>싱글톤 패턴 디자인
1단계 : 생성자를 private으로 만들기
2단계 : 클래스 내부에 static으로 유일한 인스턴스 생성하기
3단계 : 외부에서 참조할 수 있는 public 메서드 만들기
4단계 : 실제로 사용하는 코드 만들기



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ4Njk1OTkyMCwxMjAwOTE2Mjc5LC01MT
c3OTg4MTIsMTE4MzAzMzgzNSwtMTExNDAwOTU1OSwxNDkyMjI2
OTc2LDIwOTQzOTQzNzUsLTExMzgwNDgwMzIsLTM4ODA1MTQwMC
wxMzQzNDgyMTk3LDExODE4NDAzMzEsOTUwNDExMzU3LDE3Mzc5
Njg3ODksMTQ3OTYwMjUzLDU2ODIyMjI3NiwtODc1NDkwOTM3LD
I3NjI1MzYxLC0xMjY4NDgzODg1LDE2NzQ2Mzc4NTksMTA0OTE2
MTg5NV19
-->