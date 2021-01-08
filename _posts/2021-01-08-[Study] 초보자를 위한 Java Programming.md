---
title: "[Study] 초보자를 위한 Java Programming"
categories:
    - dev
tags:
    - dev
    - java 
toc: true

---

# [Study] 초보자를 위한 Java Programming

# 11장 쓰레드

* 프로세스 :: CPU가 실행 중인 프로그램(명령어) : 구성요소 = 명령어+데이터
* 멀티 프로그래밍 :: 하나의 CPU가 여러 프로그램을 동시에 실행하는 것
* 멀티 프로세싱 :: 2개 이상의 CPU에 의해 여러 개의 프로그램이 동시에 실행되는 것
* 멀티 태스킹 :: 멀티 프로그래밍과 비슷한 개념으로, 여러 개의 task를 동시에 실행하는 것
* 스레드 :: 프로세스 내에서 실행되는 세부 실행 단위
* 멀티 스레드 :: 하나의 프로세스에 내에서 여러 개의 스레드가 병행 처리되는 것
* 싱글 스레드 :: 여러 스레드가 순차적으로 실행되는 것
* 스레드의 장점 :: 코드의 재사용성과 데이터 공유가 가능하다
* 스레드의 단점 :: 여러 스레드가 동시 실행 시 공유 자원에 대해 동기화를 해주어야 한다.
* CPU 스케줄링 :: 운영체제가 작업을 처리하기 위해 각 프로세스에 CPU를 적절히 할당하는 정책
* CPU 스케줄링 종류 : 선점 (우선순위) vs 비선점 (끝까지 기다림)
* 스레드 스케줄링 :: 멀티 스레드가 동작할 때 어떤 스레드를 먼저 수행할 것인지를 결정하는 작업 / 자바는 우선순위가 높은 스레드가 먼저 실행되는 선점형 스케줄링 방식을 사용함.
* 자바 스레드 특징 :: 우선권 스케줄링 , 스레드는 각 상태를 거치면서 실행한다. 멀티 스레드로 동작한다.
* 자바에서 스레드 생성 방법 :: 1) Thread 클래스 이용 2) Runnable 인터페이스 이용 (Runnable 이 Thread를 상속함)
 
>사용자가 정의 스레드를 만드는 방법

```Java
class 클래스명 extends Thread{
	public void run(){
	//스레드 실행시 실행 명령문
	...
	}
}
```
 ⇒ 보통 Runnable 인터페이스를 이요하는 이유는 자바는 단일 상속만 허용하므로 클래스가 다른 클래스를 상속받는 경우에는 Thread 클래스를 상속받지 못함.

```Java
public class 클래스명 implements Runnable{
	public void run(){
		...
	}
}
```

 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYzNDA4MTEyNyw1MDQ3MTQ0NCwxOTY3Mj
c4Nzc5LC0xMjY0NDQ0NzczXX0=
-->